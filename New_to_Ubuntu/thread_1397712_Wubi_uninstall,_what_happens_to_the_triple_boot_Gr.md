---
title: "Wubi uninstall, what happens to the triple boot Grub?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by nooby on 2010-02-03
Edit, thnaks indeed for helpingme out with this one. 
I had triple boot but have now dual boot Vista and Frugal iso boot install of Ubuntu 9.10 using Neogrub. Yes I know that 910 are into grub2 but this is iso boot install and grub2 is needed when one do full install. 

I have triple boot and want to get rid of the ubuntu install via Wubi and instead only use Neogrub. But that one are now the third grub??? triple boot 

Vista
ubuntu via wubi
Neogrub chainloading most likely to the grub that wubi set up. 

So when I uninstall wubi should I then use Neogrub to re
add again to Vista and how does one do that? I asked on Neogrub forum but my poor english seems to have them not getting what I asked no answer. 

so I hope somebody here have already done this or or get what would happen. Can I just uninstall and then do Neogrub again? 

All this is very new to me. What should I avoid to do to not destroy the Vista install? Very important to me.

---

### Post by nooby on 2010-02-13
I wish somebody who have done this could help me. 

I have triple boot now. So wubi being the first choice after windows is the holder of the grub. so when I uninstall it doesn't the grub chainloading get broken and me have to join them together again? And when I do this. Does that write over the MBR?

---

### Post by meierfra. on 2010-02-13
Lets check out your setup. Follow these [instruction]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt.

---

### Post by nooby on 2010-02-14
I did my best to follow the instructions but that failed. Most likely due to being too complicated to tell where the file is. 

downloads is translated to Swedish so the name of that directory is /home/hämtningar instead of /home/downloads/ 

I tested both in Terminal but it gave an error that the file does not exists. No results was produced. 

Does one have to execute it from the CLI are there no other way? I know where it is can I not just run it? 

Why does the bash have to know the path via CLI. 

I know the path and can go there and tell bash this is the file I want you to bash 

~/ I can do this here but it fails in the CLI so I had to copy it from here

could that have changed something. 

What in the expected result is it you have to know. I can copy menu.lst and such 

first only Vista existed then I run the Ubuntu using wubi install so there you know what wubi does to a vista install. Then I run/ran NeoGrub which is a Gui for Grub4Dos with some variation maybe but basically the same and that one added the triple boot entry and there I have the frugal install. 

I am in wubi Ubuntu now.

---

### Post by meierfra. on 2010-02-14
> ~/ I can do this here but it fails in the CLI so I had to copy it from here


Try this. Move the script to the desktop and then
```
cd
sudo bash Desktop/boot_info_script*.sh
```

---

### Post by nooby on 2010-02-14
That one worked very well indeed. 

Very big file. I prefer to send it in PM to you and if you need to quote relevant info from it to explain to others what will happen that is ok I guess but it tell things about my HDD that maybe would open the machine up to unwellcomed visitors? Could I send pm?

---

### Post by meierfra. on 2010-02-14
> but it tell things about my HDD that maybe would open the machine up to unwellcomed visitors? 
Usually not. But sending it via pm is fine.

---

### Post by nooby on 2010-02-14
the file was too big so I tried to make two pm and sent them to you. 

Late at night here so I look for any comments or advice tomorrow some 10 hours from now.

---

### Post by meierfra. on 2010-02-14
As far as I can see you should be able to   uninstall Wubi without  causing problems for your other OS. Wubi 9.10 actually uses Grub 2 and not Grub4Dos.
Just to make sure, lets have a look at your Window 7 boot loader:

Boot into Win 7.  Click on "Start". Type "cmd" and press "Ctrl+Shift+enter". This will open  the Window 7 command line with administrative rights. Type

```
bcdedit
```

and post the output.

---

### Post by nooby on 2010-02-15
Thanks indeed for taking time to look into it. I try to do the bcedit thing. 

My worry is this. I go to Add or uninstall programs and uninstall Wubi. 

1. Either it leave a grub behind and all works as normal with a triple choice but ubuntu not there but my neogrub still there. 

2. Or it takes away the its own wubi grub and the chainloading to the Neogrub enter will break. 

3. And when I go into Neogrub and try to establish that again that action is the one overwriting the MBR resulting in me loosing contact with Vista and have to do recovery of everything? 

4. The reason I used wubi was that Ago. here in Ubuntu forum who develop wubi after tuxcantfly left it he has seen to to that wubi doesn't do bad things with Vista. There is a kind of grub backup file somewhere that restore what wubi did. And it is that action that break the chain. 
But if I do a manual uninstall instead of an automatic uninstall then it will not break. I just edit out the wubi entry in the grub. 

But I do as you say to and send it to you. 

How typical: It did not allow me to do what you described. Tested it three times. 

But I guess easybcd found same info. 

> There are a total of 3 entries listed in the bootloader.

Default: Microsoft Windows Vista
Timeout: 10 seconds.
Boot Drive: C:\

Entry #1
Name: Microsoft Windows Vista
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {35072ff7-eff3-11de-9564-002197267711}
Drive: C:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr

Entry #3
Name: NeoGrub Bootloader
BCD ID: {35072ff8-eff3-11de-9564-002197267711}
Drive: C:\
Bootloader Path: \NST\NeoGrub.mbr

[B]I mean there is my answer is it not?

my purpose is to save vista and the neogrub set up that I have but to uninstall wubi. so if I do the following:  

I could edit this one with Easybcd and manually take away wubi from HDD and not do it automatically? That way all stay as early except that I don't have to worry about having an extra layer in the boot?[/B]

The only bad thing is that I lose the 17GB loop thing that wubi created. I must find the thread describing how one get those safely back to vista? 

I guess Ago describe it somewhere. I loose one such every uninstall?

---

### Post by meierfra. on 2010-02-15
> I go to Add or uninstall programs and uninstall Wubi.

1. Either it leave a grub behind and all works as normal with a triple choice but ubuntu not there but my neogrub still there. 

That's what's going to happen. There is not connection between NeoGrub and Wubi.


> And when I go into Neogrub and try to establish that again that action is the one overwriting the MBR resulting in me loosing contact with Vista and have to do recovery of everything?
Reinstalling NeoGrub  via Easybcd does not change the MBR. It just adds an entry to the BCD. Anyway, you won't have to reinstall NeoGrub.

> But I guess easybcd found same info. 

Yes, that's essentially the same.

> I could edit this one with Easybcd and manually take away wubi from HDD and not do it automatically? That way all stay as early except that I don't have to worry about having an extra layer in the boot?
Yes you can delete everything manually.   But I would use Add/Remove programs. Sometimes that leaves the wubi entry in the bcd. But you can use "EasyBCD" to delete it.


> The only bad thing is that I lose the 17GB loop thing that wubi created. I must find the thread describing how one get those safely back to vista?
Uninstalling Wubi via Add/Remove or  manually  deleting the Ubuntu folder is all you need to do to get the 17GB back

---

### Post by nooby on 2010-02-15
> There are a total of 2 entries listed in the bootloader.

Default: Microsoft Windows Vista
Timeout: 10 seconds.
Boot Drive: C:\

Entry #1
Name: Microsoft Windows Vista
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: NeoGrub Bootloader
BCD ID: {35072ff8-eff3-11de-9564-002197267711}
Drive: C:\
Bootloader Path: \NST\NeoGrub.mbr

I did as you suggested but taking responisibility for my action and not blaming you :) 

That is what the EasyBCD show now and now to the big test. 

I do a reboot and see if it just work. and hopefully are back within 5 minutes at most and in frugal install of ubuntu

**Edit**

yes and it worked very well. Now I only need to find a way to save changes to the ubuntu 910 install. 

I can use xmarks as an addon to Firefox and that way remember bookmarks but changes to the ubunty I need some kind of back up going. 

Either Sbackup or Remastersys and that way get everything that changes back each time. 

To get Swedish kbd I use Alt+F2 and sudo setxkbdmap se that is the fastest way to achieve it. 

but why does it only work for Desk2 instead of Desk 1?

---

