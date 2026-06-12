---
title: "removing virus from pen drive"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by salima on 2010-08-25
what is the best program to use (free) that will remove the autorun and exe virus programs that get stuck on my pen drive whenever i give it to other people? i can't delete those files and i dont want to be responsible for giving them to someone else who has unreliable protection (lots of people i know.

i want something that will automatically detect and delete any virus or mallware that is on a pen drive either automatically or on demand.

i am using ubuntu 8.10 and soon to upgrade to 10.04.

---

### Post by Rubi1200 on 2010-08-25
> **salima said:**
> what is the best program to use (free) that will remove the autorun and exe virus programs that get stuck on my pen drive whenever i give it to other people? i can't delete those files and i dont want to be responsible for giving them to someone else who has unreliable protection (lots of people i know.

i want something that will automatically detect and delete any virus or mallware that is on a pen drive either automatically or on demand.

i am using ubuntu 8.10 and soon to upgrade to 10.04.
Are you saying that you use Ubuntu and give the pen drive to friends who use Windows and who then give it back to you with viruses?

If it were me, I would not be giving the pen drive to those people!

To answer the question:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Hope this helps.

---

### Post by gandaran on 2010-08-25
> **salima said:**
> what is the best program to use (free) that will remove the autorun and exe virus programs that get stuck on my pen drive whenever i give it to other people? i can't delete those files and i dont want to be responsible for giving them to someone else who has unreliable protection (lots of people i know.

i want something that will automatically detect and delete any virus or mallware that is on a pen drive either automatically or on demand.

i am using ubuntu 8.10 and soon to upgrade to 10.04.
open nautilus as root (gksu nautilus) then navigate to the pen drive and delete the autorun or any file (enable show hidden files as the .exe virus files are not normally shown), no need for antivirus when you can easily delete everything in the pen drive.

---

### Post by endotherm on 2010-08-25
last time i dealt with this kind of issue, I jsut used a windows AV scanner to clean it up (the bootsec/mbr as well). I think I was using kaspersky at the time.

---

### Post by inameiname on 2010-08-25
Haha, I second that, Rubi1200! Should do some scolding to them!. :P

Well, Clamav should work for you. It scans for viruses for both Windows and Linux, so you can just scan the drive whenever you hook it up. If not installed already, just do this in the terminal:

sudo add-apt-repository ppa:ubuntu-clamav/ppa
sudo aptitude update
sudo aptitude install clamav clamav-base clamav-daemon clamav-freshclam clamtk

UPDATE:

I agree with gandaran, just open the root nautilus and delete them that way. Sounds like the first choice to me. His posting wasn't there when I was writing mine. Hehe

---

### Post by ajgreeny on 2010-08-25
Why do people to whom you give the drive need to add anything to it in the first place, or do they not know this is happening?  Have you asked them what is happening to the disk while they have it, and what they are doing with it?  Are they passing files of some sort to you for a good reason?

If it were me, I would firstly check that the Autorun file is indeed a virus, as many are detected as viruses when they are quite innocent.  Similarly the .exe files, but it still does not answer the question as to why those files are added to the disk by someone other than yourself.

But I agree with others who have posted. Enable the Delete option in **gksudo nautilus** right click menu, and then with care, delete all files that are not needed using that right click menu.

---

### Post by inameiname on 2010-08-25
You know it's funny how we all have commented on how the others have been putting on the viruses each and every time you dish out your drive to them, but you know what....I got the perfect solution: just leave the viruses on there. They put them on, they can handle the viruses. Haha. Not like it'd affect your Ubuntu anyway. :P

---

### Post by gandaran on 2010-08-25
> **ajgreeny said:**
> Why do people to whom you give the drive need to add anything to it in the first place, or do they not know this is happening?  Have you asked them what is happening to the disk while they have it, and what they are doing with it?  Are they passing files of some sort to you for a good reason?

If it were me, I would firstly check that the Autorun file is indeed a virus, as many are detected as viruses when they are quite innocent.  Similarly the .exe files, but it still does not answer the question as to why those files are added to the disk by someone other than yourself.

But I agree with others who have posted. Enable the Delete option in **gksudo nautilus** right click menu, and then with care, delete all files that are not needed using that right click menu.
the autorun file is not a virus, it is just a modified autorun file put there along with the virus by an infected windows computer so it will facilitate infecting another windows computer when the pen drive is inserted.
autorun can and should be disabled in the windows computer to prevent infections from usb drives.

---

### Post by TNT1 on 2010-08-25
> **ajgreeny said:**
> Why do people to whom you give the drive need to add anything to it in the first place, or do they not know this is happening?  Have you asked them what is happening to the disk while they have it, and what they are doing with it?  Are they passing files of some sort to you for a good reason?  Look at it this way...  I give a flash drive to a colleague to get, dunno, pictures from the mountain bike race I did with him over the weekend, that his girlfriend took, and are on his PC. He copies a folder onto my usb thingy. Later that day, I am with a customer, and he needs to give me a backup copy of his website cause he is changing ISP's to me, and he needs me to get something live ASAP. All I have is that same usb thingy that I haven't even looked at yet. What if my colleague's PC is infected and he doesn't know it? What if his girlfriend put the pics on yet another usb thingy to put on his PC, and her PC or usb thingy is infected?  Maybe this chain shouldn't happen, but it does...  (PS, that's a true story kids...)

---

### Post by gandaran on 2010-08-25
salima
you can vaccinate the pen drive so it wont get infected when connected to the infected windows computer.
[http://www.pandasecurity.com/homeusers/downloads/usbvaccine/](http://www.pandasecurity.com/homeusers/downloads/usbvaccine/)
this little application puts a modified autorun file in the pen drive that prevents autorun from running and infecting the pen drive.

---

### Post by uRock on 2010-08-25
Deleting the autorun file on my thumb drive never works, it is there again when reinserted. 

As for the viruses, just install ClamAV and use it to scan the thumb drive every time you get it back from a Windows user.

---

### Post by TNT1 on 2010-08-25
> **uRock said:**
>  As for the viruses, just install ClamAV and use it to scan the thumb drive every time you give it to a windows user  appears to be correct etiquette...

---

### Post by Grenage on 2010-08-25
> **TNT1 said:**
> All I have is that same usb thingy that I haven't even looked at yet. What if my colleague's PC is infected and he doesn't know it? What if his girlfriend put the pics on yet another usb thingy to put on his PC, and her PC or usb thingy is infected?  Maybe this chain shouldn't happen, but it does...  (PS, that's a true story kids...)

What if it's full of hardcore porn?

I'd keep my work and home drives separate, but maybe that's just me.  Clam AV is quite good at cleaning drives.

---

### Post by TNT1 on 2010-08-25
> **Grenage said:**
> What if it's full of hardcore porn?  Then maybe you have other viruses you should be worrying about? Dunno...

---

### Post by TNT1 on 2010-08-25
> **Grenage said:**
>   I'd keep my work and home drives separate,    Yeah, like I said, the things I did probably shouldn't have happened, but two things, my flash thingy was freshly formatted when pic folder arrived on it, second, I don't mind my customer (who sponsors my mtb team) seeing those pics... Oh, wait, third, I only had that drive with me, and I am a human being...

---

### Post by uRock on 2010-08-25
> **TNT1 said:**
> appears to be correct etiquette...

Why would I scan before giving it to someone? I don't download viruses, the days of Kazaa are long gone.

---

### Post by TNT1 on 2010-08-25
> **uRock said:**
> Why would I scan before giving it to someone? I don't download viruses,   > **wacky_sung said:**
> In Ubuntu,there is a clam antivirus.You can always scan it before you passed any data.This is just a ethical way of doing so by perform a virus scan prior you hand over any data to the next person.   Dude, I had the same question, and this was the only answer I got...

---

### Post by uRock on 2010-08-25
> **TNT1 said:**
> Dude, I had the same question, and this was the only answer I got...

That's just wacky(pun intended). I do not expect others to protect my system, but if I thought I may be sharing infected data, then I would gladly scan it. My thumb drive consists of pictures taken from my camera and documents written by me or trusted sources, so I worry not.

I have also found myself having less friends with Windows as they are dumping MS for Apple and/or Ubuntu.

---

### Post by salima on 2010-08-25
i want a program that works in linux to detect and remove viruses etc from pen drives, cameras, ipod, etc without having to install a full program that will load at startup. 

is there a substitute for iKill, USB Threat Defender, etc that i can use or a way of getting the download to install on ubuntu 8.10 aaaand/or 10.04?

---

### Post by uRock on 2010-08-25
Didn't your last thread answer that? [http://ubuntuforums.org/showthread.php?t=1560806](http://ubuntuforums.org/showthread.php?t=1560806) > **salima said:**
> what is the best program to use (free) that will  remove the autorun and exe virus programs that get stuck on my pen drive  whenever i give it to other people? i can't delete those files and i  dont want to be responsible for giving them to someone else who has  unreliable protection (lots of people i know.

i want something that will automatically detect and delete any virus or  mallware that is on a pen drive either automatically or on demand.

i am using ubuntu 8.10 and soon to upgrade to 10.04.
If you needed clarification, then all you had to do was say so in the old thread(which you never responded to).

---

### Post by Iowan on 2010-08-25
Threads merged.

---

### Post by salima on 2010-08-26
> **uRock said:**
> Didn't your last thread answer that? [http://ubuntuforums.org/showthread.php?t=1560806](http://ubuntuforums.org/showthread.php?t=1560806) 
If you needed clarification, then all you had to do was say so in the old thread(which you never responded to).

i am so sorry-and embarrassed. i must have forgot to subscribe to that thread and then forgot i did it...i am trying to get myself together...i love ubuntu very much and so excited and tired and want to get down to work already. solving problems or looking for answers i mean from others is fun, but i have work to do!

i am not really as stupid as i am forgetful...

---

### Post by salima on 2010-08-26
> **gandaran said:**
> open nautilus as root (gksu nautilus) then navigate to the pen drive and delete the autorun or any file (enable show hidden files as the .exe virus files are not normally shown), no need for antivirus when you can easily delete everything in the pen drive.

here is what i put in the terminal but i must be doing something wrong-
  	 	 	 	 	 	  salima@salima-desktop:~$ gk su nautilus 
 bash: gk: command not found 
 salima@salima-desktop:~$ sudo bash 
 [sudo] password for salima:  
 root@salima-desktop:~# gk su nautilus 
 bash: gk: command not found 
 root@salima-desktop:~#

---

### Post by salima on 2010-08-26
> **uRock said:**
> Deleting the autorun file on my thumb drive never works, it is there again when reinserted. 

As for the viruses, just install ClamAV and use it to scan the thumb drive every time you get it back from a Windows user.

you delete it with nautilus and it still comes back?

i have to go to cybercafes sometimes and friends of friends want to copy things and i am always more worried they will never give the pen drive back. but then if i want to use it again it will be full of these autorun files that i have to try and find my stuff mingled with. i read about clam and they say it doesnt deal with the autorun issue, but works on viruses. the autorun programs will still mess up someone else's machine, right? 

i only consider the ethics of this in that i believe not only for my own convenience do i want to get those things off my pen drive, but why should i spread around more misery even if it can be prevented by someone else?

---

### Post by uRock on 2010-08-26
The autorun file on my thumb drive is for the U3 system. The only thing I haven't tried is deleting it via CLI, which now that it came to mind I will give it a try in the morning.

---

### Post by salima on 2010-08-26
> **gandaran said:**
> salima
you can vaccinate the pen drive so it wont get infected when connected to the infected windows computer.
[http://www.pandasecurity.com/homeusers/downloads/usbvaccine/](http://www.pandasecurity.com/homeusers/downloads/usbvaccine/)
this little application puts a modified autorun file in the pen drive that prevents autorun from running and infecting the pen drive.

does it delete the files or just immobilise them? i think in time they will become quite cumbersome and annoying if they arent removed...

---

### Post by salima on 2010-08-26
in the meantime i am getting clam, but it appears it will take some time to load...at least the command lines were accepted, i am happy about that!

also i see there are a lot of issues about pen drives, i have to learn about them. one file is called recycler and some people seem to think it is a virus and others think it is important, but it wasnt there in the beginning. i cant delete it so i think i better read more about it.

the other pen drive had some goofy things on it and one cybercafe with a virus program cleaned it up for me so i know they were viruses-one was some stupid harry potter thing and another was 'ciao'...

---

### Post by gandaran on 2010-08-26
> **salima said:**
> here is what i put in the terminal but i must be doing something wrong-
  	 	 	 	 	 	  salima@salima-desktop:~$ gk su nautilus 
 bash: gk: command not found 
 salima@salima-desktop:~$ sudo bash 
 [sudo] password for salima:  
 root@salima-desktop:~# gk su nautilus 
 bash: gk: command not found 
 root@salima-desktop:~#

**gksu nautilus** not gk su nautilus

---

### Post by gandaran on 2010-08-26
> **salima said:**
> does it delete the files or just immobilise them? i think in time they will become quite cumbersome and annoying if they arent removed...
no it wont delete anything, (you have to clean the pen yourself) only put a modified autorun file in the pen so next time the pen is inserted in an infected windows computer autorun is prevented from running then the infected computer wont be able to pass out the virus.

---

### Post by waterboy0911 on 2010-09-16
hey I just install Clamav 

but I don't know how to use Clamav to remove this files.. 

I install Clamav because I have this issue that I can't delet autorun.inf files.. or my pen drive is protected.. My pen drive has no switch to lock my pen drive. 

I have this error

```


root@jerald-laptop:/media/BC49-8C45# rm autorun.inf
rm: cannot remove `autorun.inf': Read-only file system
root@jerald-laptop:/media/BC49-8C45# rm autorun.inf 
rm: cannot remove `autorun.inf': Read-only file system

```

Please Help greatly appriciated

---

### Post by wilee-nilee on 2010-09-16
> **waterboy0911 said:**
> hey I just install Clamav 

but I don't know how to use Clamav to remove this files.. 

I install Clamav because I have this issue that I can't delet autorun.inf files.. or my pen drive is protected.. My pen drive has no switch to lock my pen drive. 

I have this error

```


root@jerald-laptop:/media/BC49-8C45# rm autorun.inf
rm: cannot remove `autorun.inf': Read-only file system
root@jerald-laptop:/media/BC49-8C45# rm autorun.inf 
rm: cannot remove `autorun.inf': Read-only file system

```

Please Help greatly appriciated

First post eh, if you have nothing on the thumb you need just reformat it. Otherwise start a thread and give us a little more information, like what is in there what you think the problem is ie virus etc. Also not sure why your in root either. Do you always run in root or is it a distro that runs in root like puppylinux.

Is the thumb a sandisk with U3 firmware?

---

### Post by waterboy0911 on 2010-09-18
> **wilee-nilee said:**
> First post eh, if you have nothing on the thumb you need just reformat it. Otherwise start a thread and give us a little more information, like what is in there what you think the problem is ie virus etc. Also not sure why your in root either. Do you always run in root or is it a distro that runs in root like puppylinux.

Is the thumb a sandisk with U3 firmware?

here is my second post.. hehehe

about the root.. I just assuming that with root I can remove the file..

about format.. Yeah I don't have important files but the issue also is that I can't even format my thumdrive.. the autorun.inf is not a virus actually but by the help of autorun.inf it will lunch the virus this is in the case of windows.. but I use ubuntu just to rid off this files.. 

I use ubuntu 10.04 with wine installed. my thumb drive is imation and it doesn't have U3 firmware.

thanks a lot for your help.

---

### Post by bodhi.zazen on 2010-09-18
> **waterboy0911 said:**
> hey I just install Clamav 

but I don't know how to use Clamav to remove this files.. 

I install Clamav because I have this issue that I can't delet autorun.inf files.. or my pen drive is protected.. My pen drive has no switch to lock my pen drive. 

I have this error

```


root@jerald-laptop:/media/BC49-8C45# rm autorun.inf
rm: cannot remove `autorun.inf': Read-only file system
root@jerald-laptop:/media/BC49-8C45# rm autorun.inf 
rm: cannot remove `autorun.inf': Read-only file system

```Please Help greatly appriciated

I assume your pen drive is either FAT or NTFS.

If you can not remove file either it is not mounted rw or your file system has errors in it.

For the first, it should be mounted rw automatically. You can check the ownership and permissions with 

```
ls -l /media
```

For the second, you are best off checking the disk from windows. If no errors are found, you could back up the data and re-format or the drive may be at or near the end of life.

---

### Post by waterboy0911 on 2010-09-18
> **bodhi.zazen said:**
> I assume your pen drive is either FAT or NTFS.

If you can not remove file either it is not mounted rw or your file system has errors in it.

For the first, it should be mounted rw automatically. You can check the ownership and permissions with 

```
ls -l /media
```

For the second, you are best off checking the disk from windows. If no errors are found, you could back up the data and re-format or the drive may be at or near the end of life.


The file system is FAT with 1GB memory 
thanks for the code it's better than my previous code
here is my old code just to get into my thumb drive
```

cd /media/ && ls

```

But is there any way that I can use force to format my pendrive? like administrator type that I can format any devices.. 

I can't remove the autorunfile.inf to all pendrive that had autorunfile.inf.. weird because last time it was just one click of a button to delet now it's locked..

---

