---
title: "Proposal for `heks`"
---

Introduction
===============================================================================

Rather than having each application handle its own keyboard shortcuts and 
events, the idea is to have a seperate application for handling them on an 
abstract, high level. Because we can focus on the keyboard interface and 
*only* that, we should handle it *well*. 

This will hopefully help to achieve consistency and enables you to obtain an 
overview of what actions you can take at any given moment, eliminating the 
steep learning curve I associate with keyboard control.

It is, of course, unlikely that `heks` will gain enough traction to be used by 
others. It will, nevertheless, be written as if it were a standard, and used 
at least by the `stilish` window manager.


Features
===============================================================================

Rough sketch of features:

Informative:

-   Each keybinding will have a description, tags, and a measure of 
    "importance" so as to generate relevant cheatsheets on-the-go, of varying 
    levels of verbosity.

-   There should always be a breadcrumb trail to indicate what mode we are 
    typing in. For example: `general > vim > view > goto<line> > g1…`


Behavioural:

-   Versatile domain-specific language (JSON or something else?) to define the 
    shortcuts.

-   Automatically attach relevant keybindings as programs open, and detach 
    them when they close.

-   There are different ways to communicate with any particular program (UNIX 
    sockets, DBUS, one-time command execution...). The library should expose 
    methods for communication and command parsing.

-   Shortcuts can be filtered: perhaps it is only active when this or that 
    program is running, or when a particular mode is active. Some modes are 
    permanent until explicitly changed, some disable all other keys, etcetera.

-   Keystrokes can be active on keydown, keyup, or even after a defined 
    keypress interval. Keys can be defined in terms of keysyms or keycodes. 
    Variables can be drawn from regexes or dictionaries, and each variable 
    comes with a "description" too. Variables can be recursive.

-   There should be a robust way to handle conflicting keybindings. (Monoid?)

-   The software should be able to respond to events that are not triggered by 
    the keyboard: spawning an X window, spawning a virtual terminal, etcetera.
