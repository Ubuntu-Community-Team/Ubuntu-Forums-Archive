---
title: "X server. Fatal server error: no screens found. NVidia 9400 card"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by antitalented on 2009-02-26
Trying to install Ubuntu Intrepid on my dell XPS 13 laptop.
I was using hardy before this. I did an Internet update. On reboot, X did not start. 

(EE) No devices detected.

Fatal server error:
no screens found

X started on Hardy but did not detect my Geforce 9400 card. Hence supported a max resolution of only 800*600 which sucked. Tried playing around with the Nvidia restricted drivers for a while but no results. Thought I would take a shot at Intrepid and see if the resolution improved. The situation has worsened. X is totally bombing out now. I have checked what ubuntuforums has to say on this topic. None of it has helped.

My /var/log/Xorg.0.log is attached.

Any kind of help would be greatly appreciated.

---

### Post by ddrichardson on 2009-02-27
Post /etc/X11/xorg.conf

---

### Post by jt_04 on 2009-03-30
I am having the same problem with the same card.  Have you found a solution yet?

---

### Post by James_Lochhead on 2009-03-30
Try this:

When the computer is booting and the grub menu comes up (if there is no menu and just a timer press esc) choose the option for recovery.

After the recovery menu comes up choose the root option. Next, run:

nvidia-xconfig

I.e. type it and press enter and follow any prompts (can't remember if there are any).

Next type;

exit

And press enter

Then choose boot normally.

That might have fixed your problem.

---

### Post by tolean_dj on 2010-12-27
Thanks a lot! That worked for me! You saved my day :)

---

### Post by Samiunn on 2011-08-20
Or someone could try to find xorg.conf.failsafe in /etc/X11/
After that you only need to copy/rename that file to xorg.conf

---

