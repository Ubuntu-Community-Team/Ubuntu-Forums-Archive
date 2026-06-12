---
title: "Odd folder/filenames through Samba"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by jtfolden on 2006-12-25
I'm sharing several volumes via my Mac mini/OS X system... Other OS X and Windows systems see these shares just fine and everything works great....

With Ubuntu 6.10/Samba, however, I'm noticing an oddity with certain folder/filenames...

Let's say I've made a Folder on the Mac called "Linux (6.10)". When I look for that folder under Ubuntu it comes across as something like "C1AXT2~f" instead.  Plenty of names look fine but there are quite a few that come across as very cryptic.

My assumption is that it MIGHT have something to do with certain characters in the filename not being valid under Linux file systems but the logical thing would be to exchange those symbols for something legible, not to make the entire name into alien gobbledygook.

Might there be a fix (other than having to rename everything)?

Thanks,
John

---

### Post by jtfolden on 2006-12-28
bump

---

### Post by huggy77 on 2007-07-03
i am having the same problem...  I think it is because you have parens in your folder name...  i have spaces in my file and folder names and i am trying to get a workaround....   any help would be great...

---

### Post by jtfolden on 2007-07-03
I never did come across with a workable solution and have since stopped using Ubuntu due to the inherent problem of not easily upgrading many apps without upgrading the whole distro.

---

### Post by huggy77 on 2007-07-03
i loaded up netatalk on the box and it took care of the issue...

i am now using apple talk to move files around from Mac to Linux...

you can find a cool tutorial here:
[http://gentoo-wiki.com/HOWTO_Share_Directories_via_AFP](http://gentoo-wiki.com/HOWTO_Share_Directories_via_AFP)

it is gentoo but works on our beloved tux distro...

to simplifly things i wrote an applescript to handle the connections....  

i am not sure if this is a real solution but we will see...

---

