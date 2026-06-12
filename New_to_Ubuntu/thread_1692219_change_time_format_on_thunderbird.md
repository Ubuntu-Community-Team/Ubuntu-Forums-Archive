---
title: "change time format on thunderbird"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by ukha on 2011-02-21
How to change time format on thunderbird + lithium (lanikai 3.1.7) on ubuntu 10.04 x64?
(from 12 to 24)

---

### Post by An Sanct on 2011-02-21
Welcome to the forum!

Well, Thunderbird should use the system locale ... should, because it doesn't :(

here is a forum post, that helps you create a launcher, that tells Thunderbird *directly* what format to use ... I will do this too, the dd/mm/yyyy american format is driving me crazy ... I'll let you know if it works in a later edit.

edit: No I couldn't make it work ... but it was worth a try...

---

### Post by ukha on 2011-02-21
I have read [this]("http://ubuntuforums.org/showthread.php?t=595982") and [this]("http://ubuntuforums.org/showthread.php?t=829029") and [this]("http://lildude.co.uk/howto-customise-thunderbird-date-format") and tried:
[INDENT] export LC_ALL=en_GB.utf8
thunderbird
[/INDENT]It works!
Thank you for your information!

---

### Post by ksciur on 2012-04-13
I have also found this solution. To always launch with the correct date format, I've done:
Open Menu Editor and Edit the thunderbird Icon and add this in the command to launch the program:
export LC_TIME=en_GB.UTF-8 && thunderbird %u

:guitar: works like a charm in Thunderbird 11.0.1

---

### Post by Cobalto on 2012-08-18
I run into that sort of thing constantly, so I opened an Ubuntu Brainstorm idea to get it fixed: [http://brainstorm.ubuntu.com/idea/30055/](http://brainstorm.ubuntu.com/idea/30055/) See if you like it, comment and vote.

---

