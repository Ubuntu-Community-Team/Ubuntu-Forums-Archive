---
title: "update bricked some programs"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by morgonzola on 2010-01-11
hello i recently just did a round of updates and for some odd reason it made 2 programs not open. the ubuntu software center and midori web browser. i am running ubuntu 9.10 and as previously stated have completely updated my system. i have already used synaptic to do a reinstall of these two programs and that didnt fix the problem. any ideas as to whats wrong?

---

### Post by Sef on 2010-01-11
Have you gone into Synaptic and checked Fix Broken Packages (under Edit)?

---

### Post by Hospadar on 2010-01-11
Try starting them in a terminal and see if they give you any interesting error messages.

Sometimes a new update doesn't play nice with old configuration files, and clearing out the old configuration files will solve the issue.  Depending on the program these will be located in different places, but typically will reside in some hidden folder in the home directory.

---

### Post by morgonzola on 2010-01-11
> **Sef said:**
> Have you gone into Synaptic and checked Fix Broken Packages (under Edit)?

yes i have tried this and it still doesn't fix the problem. i even tried to uninstall completely and get rid of all the config files through synaptic and then reinstall, but that didn't work out either

---

### Post by morgonzola on 2010-01-11
> **Hospadar said:**
> Try starting them in a terminal and see if they give you any interesting error messages.

Sometimes a new update doesn't play nice with old configuration files, and clearing out the old configuration files will solve the issue.  Depending on the program these will be located in different places, but typically will reside in some hidden folder in the home directory.

by interesting error message do you mean this?

midori: symbol lookup error: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

---

### Post by sandyd on 2010-01-11
> **morgonzola said:**
> by interesting error message do you mean this?

midori: symbol lookup error: /usr/lib/libwebkit-1.0.so.2: undefined symbol: soup_content_decoder_get_type

[http://art.ubuntuforums.org/showthread.php?t=1374832](http://art.ubuntuforums.org/showthread.php?t=1374832)

---

### Post by morgonzola on 2010-01-11
> **carlee said:**
> [http://art.ubuntuforums.org/showthread.php?t=1374832](http://art.ubuntuforums.org/showthread.php?t=1374832)

thanks for the link guess i didn't check the treads as thoroughly as i should have

---

