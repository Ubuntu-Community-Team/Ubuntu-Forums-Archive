---
title: "java wont run since upgrade"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-04-29
just upgraded and now when I visit a website that uses an embedded video it informs me I am missing a plugin, when I ask for it to offer suggestions it says it has none to offer I do have ubuntu restricted extras installed though

---

### Post by Geoff918 on 2010-04-29
Are you sure it's installed? Many of these things are disabled upon upgrade.

From command line (CLI) enter the following

aptitude search ubuntu-restricted-extras

if has an 'i' in front of the file then it truly is installed. If it has 'p' or something else then it is not truly installed.

---

### Post by LunaticHiatus on 2010-04-29
i   ubuntu-restricted-extras

I downloaded the flash plugin by itself so flash videos are playing, but its very odd that the browser doesnt seem to think it is. my .mkv's work and whatnot

---

### Post by ddecator on 2010-04-30
The Ubufox Firefox extension does not properly point users to where Flash is available yet. It's a known issue and is being worked on.

---

