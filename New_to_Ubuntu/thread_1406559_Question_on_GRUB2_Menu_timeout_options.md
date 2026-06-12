---
title: "Question on GRUB2 Menu timeout options"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-02-14
So, I'm playing around with some options in /etc/default/grub (specifically, GRUB_HIDDEN_TIMEOUT and GRUB_TIMEOUT).

GRUB_TIMEOUT seems to be pretty intuitive, but GRUB_HIDDEN_TIMEOUT is the one that stumps me. The community docs say that option hides the menu for the specified number of seconds, and pressing shift during that timeout will show the menu.

I changed the value to 10, 0, and -1, but GRUB_HIDDEN_TIMEOUT does not seem to have any effect during boot. I held shift on several tries, but all of them seem to play no effect on the menu.

I have changed all the values almost back to the way they were (commented GRUB_HIDDEN... and set GRUB_TIMEOUT to 3 instead of 10).

So, what does GRUB_HIDDEN_TIMEOUT supposed to exactly do?

EDIT: Also, I definitely ran "sudo update-grub2" after each edit of /etc/default/grub. This brings up another question: is there any difference between update-grub2 and update-grub for me?

EDIT #2: I think I found the reason why GRUB_HIDDEN_TIMEOUT doesn't do a thing. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) says that as long as I have another OS, the menu will always show.

---

### Post by audiomick on 2010-02-14
I _think_ you have understood the GRUB_HIDDEN_TIMEOUT correctly. If find the entry on the topic here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
a little clumsy and hard to understand.

Maybe you could try pressing shift repeatedly instead of holding it down.

As far as the "update" command goes, in the documentation I have only seen reference to
> "update-grub" run as root and referneces to "update-grub2" only in posts in the forum. I would go for that which I have seen in the documentation, but I am not an expert...

You could also look at this
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by rnerwein on 2010-02-14
> **audiomick said:**
> I _think_ you have understood the GRUB_HIDDEN_TIMEOUT correctly. If find the entry on the topic here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
a little clumsy and hard to understand.

Maybe you could try pressing shift repeatedly instead of holding it down.

As far as the "update" command goes, in the documentation I have only seen reference to
 and referneces to "update-grub2" only in posts in the forum. I would go for that which I have seen in the documentation, but I am not an expert...

You could also look at this
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
hi
the answer of your question about update-grub2 is:
update-grub2  is  a stub for running update-grub which itself is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to  generate a grub2  config file.

ciao

---

### Post by audiomick on 2010-02-14
> **rnerwein said:**
> hi
the answer of your question about update-grub2 is:
update-grub2  is  a stub for running update-grub which itself is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to  generate a grub2  config file.

ciao
Danke!

---

### Post by drs305 on 2010-02-14
> **mathfreak123 said:**
> So, what does GRUB_HIDDEN_TIMEOUT supposed to exactly do?

EDIT #2: I think I found the reason why GRUB_HIDDEN_TIMEOUT doesn't do a thing. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) says that as long as I have another OS, the menu will always show.

GRUB_HIDDEN_TIMEOUT is meant to display a blank screen for a given number of seconds. The GRUB_HIDDEN_TIMEOUT_QUIET entry is to show or hide a countdown timer.

As has been discussed, the way the G2 scripts were written the hidden menu option is available only if there is one OS present. If you have multiple OS's, the menu will be displayed and you can't hide the menu with the grub.cfg settings. I don't like this philosophy but I'm just a user and wasn't asked.  ;-)

You can, however, edit the /etc/grub.d/30_os-prober script to get a hidden menu even with multiple OS's. If you want that I can tell you how. I'll also add it to my Grub 2 Title Tweaks thread when I get a chance.

Also, I agree with *audiomicik* that the community doc describing the timeout settings could be clearer. I will rewrite that doc when Lucid packages are "frozen" so I can update it with information relevant to the Ubuntu 1.98 version of Grub.

---

### Post by mcduck on 2010-02-14
> **drs305 said:**
> GRUB_HIDDEN_TIMEOUT is meant to display a blank screen for a given number of seconds. The GRUB_HIDDEN_TIMEOUT_QUIET entry is to show or hide a countdown timer.

As has been discussed, the way the G2 scripts were written the hidden menu option is available only if there is one OS present. If you have multiple OS's, the menu will be displayed and you can't hide the menu with the grub.cfg settings. I don't like this philosophy but I'm just a user and wasn't asked.  ;-)

You can, however, edit the /etc/grub.d/30_os-prober script to get a hidden menu even with multiple OS's. If you want that I can tell you how. I'll also add it to my Grub 2 Title Tweaks thread when I get a chance.

Also, I agree with *audiomicik* that the community doc describing the timeout settings could be clearer. I will rewrite that doc when Lucid packages are "frozen" so I can update it with information relevant to the Ubuntu 1.98 version of Grub.

Actually there's nothing stopping you from hiding the menu, not even on a dualboot system.

Just set GRUB_TIMEOUT to "0" and GRUB_HIDDEN_TIMEOUT to whatever you want (and GRUB_HIDDEN_TIMEOUT_QUIET to true if you don't want the counter).

The point is that you must set the normal timeout value to zero, otherwise the menu won't hide no matter what you do with the other options.

(I haven't edited any of the scripts under /etc/grub.d/, and I have a diual-boot setup with a hidden Grub menu.)

---

### Post by mathfreak123 on 2010-02-14
> **mcduck said:**
> Actually there's nothing stopping you from hiding the menu, not even on a dualboot system.

Just set GRUB_TIMEOUT to "0" and GRUB_HIDDEN_TIMEOUT to whatever you want (and GRUB_HIDDEN_TIMEOUT_QUIET to true if you don't want the counter).

The point is that you must set the normal timeout value to zero, otherwise the menu won't hide no matter what you do with the other options.

(I haven't edited any of the scripts under /etc/grub.d/, and I have a diual-boot setup with a hidden Grub menu.)


I realized I could do that, but what if I want to boot my other OS (or maybe an older kernel?) (sorry if I left out the info that I have a dual-boot)? I tried holding and pressing shift while the computer was booting, but regardless of the settings I have set in /etc/default/grub, the shift key does nothing for me.

---

### Post by drs305 on 2010-02-14
> **mathfreak123 said:**
> I realized I could do that, but what if I want to boot my other OS (or maybe an older kernel?) (sorry if I left out the info that I have a dual-boot)? I tried holding and pressing shift while the computer was booting, but regardless of the settings I have set in /etc/default/grub, the shift key does nothing for me.

The problem is that the keystatus check is part of 30_os-prober and isn't checked if there is another detected OS on the computer. I recommended that the keystatus check be moved to 00_header so that with multi-OS systems or if 30_os-prober is disabled the keystatus check will still be accomplished.

If you wish, you can copy the keystatus check, without some of the conditionals, into the 00_header file so that it will check even on multi-OS systems. You would add this to the bottom of the /etc/grub.d/00_header file, save the file, and then update-grub:
> 
	cat <<EOF
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
  fi
EOF


---

### Post by mathfreak123 on 2010-02-14
> **drs305 said:**
> The problem is that the keystatus check is part of 30_os-prober and isn't checked if there is another detected OS on the computer. I recommended that the keystatus check be moved to 00_header so that with multi-OS systems or if 30_os-prober is disabled the keystatus check will still be accomplished.

If you wish, you can copy the keystatus check, without some of the conditionals, into the 00_header file so that it will check even on multi-OS systems. You would add this to the bottom of the /etc/grub.d/00_header file, save the file, and then update-grub:

This has given me the solution I wanted. Thank you very much for the help!

The grub menu doesn't load anymore unless I hold the shift key down, and this is definitely the desired effect. Again, thanks for the help! :D

---

