---
title: "How do I change grub2 menu titles?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by tuahaa on 2011-01-01
Hi!

I would like to know how to edit the grub2 menu titles...

Instead of, for example, the ubuntu entry stating the kernal number and everything, I would just like to label it as "ubuntu".

Thanks!

---

### Post by JRV on 2011-01-01
EDIT - I erased my post, the method listed below is better than mine.

---

### Post by Jeanke on 2011-01-01
Hi,

I created my own custom menu according to following instructions: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")
Works fine for me.

Grtz

---

### Post by QLee on 2011-01-01
[QUOTE=tuahaa]
I would like to know how to edit the grub2 menu titles......[/QUOTE]

A very good guide from a member of the Ubuntu community, drs305, is in this link:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by carvish on 2011-01-03
> **Jeanke said:**
> Hi,

I created my own custom menu according to following instructions: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
Works fine for me.

Grtz

Hello, I have followed the instructions from this site and do have a listing of custom in my grub loader and the booter works fine, my problem is when i try to hide the original grub screen . source forge directs you to another site, [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:#Step_1_Enable_the_Hidden_Menu_feature](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:#Step_1_Enable_the_Hidden_Menu_feature). They also say to follow only step one. For one the block of code looks like "make timeout" not the "adjust time out".
Secondly, the instructions are not too clear, quote " and looks for "adjust_timeout () {" and place a "#" in front of the second and second two last line of that block of code: " What kind of English is that? Any help would greatly be appreciated. Thank you
Carvish

---

### Post by oldfred on 2011-01-03
He gives a nice example and shows the # to make it a comment on the second line (first if) and then on the last line last fi (endif), last line is just }, so technically it is next to last line . Verbiage could be a bit more clear but example is exactly what you need to do. 

But grub2 has changed so your version may not match exactly.

---

