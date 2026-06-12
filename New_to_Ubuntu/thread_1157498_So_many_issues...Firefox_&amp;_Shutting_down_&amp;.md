---
title: "So many issues...Firefox &amp; Shutting down &amp; pages loading &amp; just plain performance.Etc"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by faron45 on 2009-05-12
Why is it that whenever I shut down firefox because it's stopped responding or,is just plain not operating properly or smoothly,when I attempt to restart it by re-opening my previous session,it seems that most of the pages do not seem to want to open completely ? Or even at all. 

 The little "status circle" that goes round & round & stops when the  page has finished loading seems to go on forever.At least until firefox has decided that it's been trying too long & then just decides to shut itself down.DAMNIT !! IS THERE ANYTHING I CAN DO TO MAKE THIS COMPUTER WORK BETTER ??? 

 I just seem to have so many problems with this thing.It seems like one thing after another. I personally don't think that xubuntu was installed properly but,what am I to do about it because it was installed by my girlfriends sisters boyfriend [who is a comp geek].

 And,I don't have a burner on this thing so I can't burn my own copy of xubuntu & try to reinstall.Although,he did give me a copy of a xubuntu cd [but,I'm afraid it may be corrupted with some sort of spyware or something.Is there anyway to tell ??] Is there anything I can do ?? As I said.I just seem to have one issue after another with this thing.Even when shutting down it tells me things aren't shutting down properly.I can't exactly tell what is not shutting down properly though because it moves right past that screen so fast ! Helppppppppppppppppp ????????????????????

 Are there any performance tests etc that I can run for this operating system,etc ??

 Oh,yes...and commands [like right clicking "open in new tab" are accepted wrong also.They are sometimes opened in a new window.Etc,etc,etc.And,what does yahooapis have to do with this site ?? Noscript tells me that yahooapis.com is part of this site.Should I allow this to run ?? And,how about google analytics ?? should I allow that to run as well ?? Hmmmmmmmmmmmmmmmmm.

---

### Post by Didius Falco on 2009-05-12
Hi faron45 - welcome to the forums!

Sorry to hear that you are having problems. Since it is a new install, it might be a good idea to install a fresh copy of it.

On the other hand, it sounds like a large part of the problems you are having are centered around Firefox. 
Yopu might try removing it and reinstalling it from Synaptic Package Manager. If you choose the "remove completely" option, be sure and back up your bookmarks and extensions first.

If you have concerns that the cd may be faulty the first thing to do is to boot with the CD and check it for errors. If none are found, it should work.

Unless your girlfriends sisters boyfriend put some spyware in it, you can be assured it doesn't have any, so long as it was downloaded from an official source.

Ubuntu has a firewall that, by default, doesn't accept any traffic in, and as long as you stick with the Open Source packages available through Synaptic, you have nothing to worry about. 


I hope things get better for you...

Regards,

Didius

---

### Post by faron45 on 2009-05-12
Thanks very Much Didius.Your advice always seems very sound.I appreciate your help very much.But,the "install" is now about a year old.Can you tell me how I would check that cd for errors ? And,how about checking it [the cd] for spyware,is that possible ?

 And,I think I've talked to you about this before but refresh please...how about those shut down errors Ikeep seeing ? Is there a way I can read all that info without it speeding by so quickly ?

---

### Post by Didius Falco on 2009-05-13
> **faron45 said:**
> Thanks very Much Didius.Your advice always seems very sound.I appreciate your help very much.But,the "install" is now about a year old.Can you tell me how I would check that cd for errors ? And,how about checking it [the cd] for spyware,is that possible ?

 And,I think I've talked to you about this before but refresh please...how about those shut down errors I keep seeing ? Is there a way I can read all that info without it speeding by so quickly ?

Hi Faron,

To check the CD itself for errors, simply set your PC to boot from CD first. It will boot to a menu with a "check CD for errors" option. Select that and it will check the to see if there are any errors on the CD itself from when it was burned.

As to your spyware worries, it's not something that could effect Ubuntu, or any linux distro and user that follows the standard security rules.

You know how you have to use "sudo" to carry out any system commands? That is a large part of what protects you.

It is possible to be infected with spyware, but you'd have to cooperate all the way, in effect, giving it permission to run.

Read this short article for a good overview of the basic differences between security models in Windows and linux:

[http://www.securityfocus.com/columnists/188](http://www.securityfocus.com/columnists/188) 

Yes, that article is a few years old, but it still holds true today - if anything, even truer, because of the frequency of updates. Since all the code is open source, anyone trying to inject spyware or other nasties into it would, in short order, be exposed.

To check the validity of the Iso the CD was burned from, you can do a Hash check. Here is a page explaining how to do just that, and a second page listing the mdD5 Hash numbers for every Ubuntu distribution:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Finally, to check on the errors you are seeing, you could have a look at your log files in **System/Administration/Log File Viewer**. A good place to start is with the messages log.

You could also try hitting the break key to pause the screen. If that doesn't work, you could edit your Menu.lst file and remove the "quiet" and "splash" setting on your kernel line.

First, open a Terminal and back up your menu.lst file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.faron1
```That will simply make a copy of your current menu.lst file with the name menu.lst.faron1 in the same directory.

To edit the file, type ```
gksudo gedit /boot/grub/menu.lst
```Here is a sample from mine:

```
title        Ubuntu 9.04 Default 2.6.28-11-generic
root        (hd0,10)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```And how it would look after I changed it:

```
title        Ubuntu 9.04 Default 2.6.28-11-generic
root        (hd0,10)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```You simple edit out the two words "quiet" and "splash".

What that does is to stop the graphical logo from showing, and it lets all the text be shown.

Then you can try the above suggestions to catch any error message, and do a search in the forums, or through a search engine, or post a message in a new thread here in the forums, to find out what they mean, and any fixes for them.

I hope this helps dispel your concerns about spyware and helps you find the errors that are giving you problems.

Regards,

Didius

---

### Post by superprash2003 on 2009-05-13
your firefox ,"open in a new tab " can be fixed this way [http://www.prash-babu.com/2009/05/how-to-fix-firefox-right-click-strange.html](http://www.prash-babu.com/2009/05/how-to-fix-firefox-right-click-strange.html)

---

### Post by Didius Falco on 2009-05-13
> **superprash2003 said:**
> your firefox ,"open in a new tab " can be fixed this way [http://www.prash-babu.com/2009/05/how-to-fix-firefox-right-click-strange.html](http://www.prash-babu.com/2009/05/how-to-fix-firefox-right-click-strange.html)

+1 on that tip, superprash. Works a treat for me, on all 5 of my installs.

Regards,

Didius

---

