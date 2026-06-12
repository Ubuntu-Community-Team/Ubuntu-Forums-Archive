---
title: "[SOLVED] Open office driving me crazy!!!!"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by aut-omatic on 2008-12-07
Well, every time I use open office, it suddenly crashes. This mostly happens when i use open office presentation. I have tried to find a pattern or something that would tell me when it will crash, but it's impossible!!! NOTHING!!! JUST AT RANDOM POINTS!!! 

So, hope you people can help me :D

---

### Post by Elfy on 2008-12-07
Not easy to tell what's going on but you could try increasing the amount of memory available for openoffice to start with

Tools - options - memory - I have Undo set at 25,  Use for oo set to 128MB, Memory per object at 6Mb.

Also next time it crashes have a look in dmesg to see if it gives an indication
```
dmesg |tail
``` will give last 10 lines, adding -20 will show last 20 lines

---

### Post by aut-omatic on 2008-12-07
ok thanks!!! I changed the memory settings, and i will let you know when it crashes again! thank you!

---

### Post by Elfy on 2008-12-07
Just come back here if it crashes - let us know what you were doing at the time and if it makes no sense to you post the dmesg output as well.

---

### Post by aut-omatic on 2008-12-07
ok, to my surprise it crashed after not very long. 
Basically what i was doing was giving some pictures some appearing options. You know when you press a button and a picture swipes in from the top corner or something. I was checking out the previews on the sidebar, and then BOOM. It crashed.

Without doing anything else, i immediately went to terminal and did the command. 
This is what came:

```
martin@martin-desktop:~$ dmesg |tail
[ 2044.841889] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2044.841907] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[ 2044.841915] sr 1:0:1:0: [sr1] Add. Sense: No seek complete
[ 2044.841923] end_request: I/O error, dev sr1, sector 104
[ 2255.615611] firefox[6681]: segfault at b7add71e ip b7e16571 sp bfab2bf4 error 4 in libc-2.8.90.so[b7de8000+158000]
[ 3530.321319] firefox[7184]: segfault at b797f71e ip b7cb8571 sp bfb56d54 error 4 in libc-2.8.90.so[b7c8a000+158000]
[ 3549.988366] firefox[7189]: segfault at b794771e ip b7c80571 sp bfb1ec64 error 4 in libc-2.8.90.so[b7c52000+158000]
[ 3832.891420] firefox[7928]: segfault at b7a9271e ip b7dcb571 sp bf96a2b4 error 4 in libc-2.8.90.so[b7d9d000+158000]
[ 4047.591889] firefox[8031]: segfault at b7abd71e ip b7df6571 sp bf8931d4 error 4 in libc-2.8.90.so[b7dc8000+158000]
[ 5424.960830] firefox[8885]: segfault at b7a3f71e ip b7d78571 sp bff15864 error 4 in libc-2.8.90.so[b7d4a000+158000]
```

---

### Post by bryncoles on 2008-12-07
i might be barking up the wrong tree here, but back when i used oipen office in windows it used to crash all the time. 

i 'fixed' the problem by going into tools, opytions, java and unselecting 'use java runtime environment.

maybe that will help?

---

### Post by ugm6hr on 2008-12-07
> **aut-omatic said:**
> Well, every time I use open office, it suddenly crashes. This mostly happens when i use open office presentation.

I have found Impress (presentation software) was pretty unstable at 2.4 (in Hardy).

3.0 has proved to be more reliable for me.

---

### Post by HotShotDJ on 2008-12-07
> **ugm6hr said:**
> I have found Impress (presentation software) was pretty unstable at 2.4 (in Hardy).

3.0 has proved to be more reliable for me.Agreed!  However, wait a little bit (hopefully only a day or two) before trying to upgrade to 3.0.  The easiest way is by adding the ppa.launchpad.net repository (see: [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive) ) but there was a problem with the last upgrade and they are now in the process of packaging and uploading the corrected packages.

Remember, those packages are only for Intrepid (8.10) and Jaunty (9.04 Development).  If your using Hardy, you'll have to use these instructions: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by aut-omatic on 2008-12-08
well, I upgraded it to 3.0. And it was surprisingly easy too! In case anyone wants too upgrade too, heres the website that helped me 

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

THANKS ALL! :D

---

### Post by zika on 2008-12-08
> **aut-omatic said:**
> well, I upgraded it to 3.0. And it was surprisingly easy too! In case anyone wants too upgrade too, heres the website that helped me 

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

THANKS ALL! :D

Does that mean that *[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)* is on again? It was empty for weeks. Did they solve the problem, i.e. the bug?

---

### Post by meho_r on 2008-12-08
I think not. There is still the warning not to follow that tutorial till repos are fixed.

EDIT: Hmm, not sure anymore? Anyone has any infos about repos? Are they fixed already?

---

### Post by HotShotDJ on 2008-12-09
> **meho_r said:**
> Hmm, not sure anymore? Anyone has any infos about repos? Are they fixed already?Yes... the repository is fixed now.  The new packages came online for Intrepid yesterday.  I updated my system with no problem -- and even prepared a lecture using the new version of Impress.  It worked perfectly.

---

### Post by crjackson on 2008-12-09
And the quickstarter tray applet is now fixed so it stays where you put it after a reboot.

---

