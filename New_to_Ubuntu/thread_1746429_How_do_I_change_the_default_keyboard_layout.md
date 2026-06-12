---
title: "How do I change the default keyboard layout?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-05-01
Unfortunately I rushed through the Ubuntu installation and picked 'Turkmenistan' as the default layout. Most letters work ok, but others look weird.

How do i change the default?? I can click on the USA layout, but when I restart my computer at all it just switches back.. :confused:

I've seen multiple threads about this that say to run a command in the terminal, but where do I go from there? Any help is appreciated.

---

### Post by jrozo17 on 2011-05-01
Anyone?

Ive tried running the command below but I have no idea what to do after. 


sudo dpkg-reconfigure console-setup

---

### Post by jrozo17 on 2011-05-01
These are my choices.. :(



 . Arabic                                                               &#8593;  &#9474;
&#9474;    # Armenian                                                             &#9646;  &#9474;
&#9474;    # Cyrillic - KOI8-R and KOI8-U                                         &#9618;  &#9474;
&#9474;    # Cyrillic - non-Slavic languages                                      &#9618;  &#9474;
&#9474;    # Cyrillic - Slavic languages (also Bosnian and Serbian Latin)         &#9618;  &#9474;
&#9474;    . Ethiopic     
 # Georgian                                                             &#8593;  &#9474;
&#9474;    # Greek                                                                &#9618;  &#9474;
&#9474;    # Hebrew                                                               &#9646;  &#9474;
&#9474;    # Lao                                                                  &#9618;  &#9474;
&#9474;    # Latin1 and Latin5 - western Europe and Turkic languages              &#9618;  &#9474;
&#9474;    # Latin2 - central Europe and Romanian                                 &#8595;  &#9474;
 # Latin3 and Latin8 - Chichewa; Esperanto; Irish; Maltese and Welsh    &#8593;  &#9474;
&#9474;    # Latin7 - Lithuanian; Latvian; Maori and Marshallese                  &#9618;  &#9474;
&#9474;    . Latin - Vietnamese                                                   &#9618;  &#9474;
&#9474;    # Thai                                                                 &#9646;  &#9474;
&#9474;    . Combined - Latin; Slavic Cyrillic; Hebrew; basic Arabic              &#9618;  &#9474;
&#9474;    . Combined - Latin; Slavic Cyrillic; Greek                             &#8595;  &#9474;
. Combined - Latin; Slavic and non-Slavic Cyrillic                     &#8595;

---

### Post by kaldor on 2011-05-01
If you are on Unity, click the power icon on the top right and press "System Settings". In that, there will be a Keyboard icon under Hardware. You can adjust stuff there.

If you are on regular GNOME Panel, you can press System > Preferences > Keyboard to get to the same thing.

There's a Layout tab that you can adjust to your liking and even make it system-wide for all users.

---

### Post by jrozo17 on 2011-05-04
> **kaldor said:**
> If you are on Unity, click the power icon on the top right and press "System Settings". In that, there will be a Keyboard icon under Hardware. You can adjust stuff there.

If you are on regular GNOME Panel, you can press System > Preferences > Keyboard to get to the same thing.

There's a Layout tab that you can adjust to your liking and even make it system-wide for all users.

Thanks for replying, I just ended up doing a full re-installation. :)

---

### Post by jmolinaso on 2011-05-08
Hi all,
I just did those steps and still when I reboot the systems falls back to the previous keyboard layout, even though I removed and applied for the system.
I also tried changing the /etc/default/keyboard manually and $ sudo dpkg-reconfigure keyboard-configuration, and still after reboot keeps both versions and the default one is BE instead of US.

I'll dig bit more and post findings.

btw: I upgraded the system from 10.10!

---

### Post by geazzy on 2011-05-08
> **jrozo17 said:**
> Thanks for replying, I just ended up doing a full re-installation. :)

wow fresh install :D

---

### Post by aasmith on 2011-05-22
Does anybody have an answer to this one? I also chose the wrong layout when I installed (I wanted USA International (AltGr dead keys), but I chose USA Alternative International), and it keeps reverting to that one whenever I reboot. I have to change this via Keyboard Preferences/Layouts *every* time I start up. This seems like a really annoying design fail. I want the wrong layout gone for good.

Thanks. :)

---

