---
title: "No Applications Found!"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-03-13
Hi everyone.

I haven't long started using Intrepid (couple of weeks) and today I connected my iPod and Cannon Digital Camera to my laptop only to be told there are No Applications Found that will connect to either device. Now with Hardy F-Spot and Banshee would automatically come up in the information box as choice but in Intrepid neither are to be found yet they are both installed.

This is quite unfortunate as I have convinced my sister to use Ubuntu and she has found the same thing happened. The first thing she said is Windows would automatically connect to the Camera but Ubuntu isn't. I know with using Hardy this Camera and iPod will connect automatically so I expected Intrepid would as well and would appreciate any help in getting it to.

Thanks in advance.

---

### Post by sgosnell on 2009-03-13
Have you installed f-spot and banshee?

---

### Post by k3lt01 on 2009-03-13
> **sgosnell said:**
> Have you installed f-spot and banshee?> **k3lt01 said:**
> Now with Hardy F-Spot and Banshee would automatically come up in the information box as choice but in Intrepid neither are to be found yet they are both installed.As you can see from my earlier post which I have quoted here the answer to your question is yes I have installed F-Spot and Banshee.

F-Spot is in the base install of Ubuntu and Banshee is my preferred application for Music etc. so it was installed before anything was updated.

---

### Post by sgosnell on 2009-03-15
Open Nautilus (you can just click on Places and select anything) then Edit Preferences.  On the Media tab, select Pictures and f-spot should be one of the choices.  Select it and it should open whenever you connect any USB device that has pictures on it.  Do the same for Music Player.  You may have to manually add Banshee, but maybe not.  That should get you working.

Sorry to be a little late in getting back, other life events going on.

---

### Post by k3lt01 on 2009-03-16
I did what you have suggested and it wont work. The relevant sections are blank and don't give any options. You mentioned doing it manually for Banshee, how do I do it? I would like to learn how to fix this for all possible applications/file formats that I use and may use in the future.

---

### Post by orethrius on 2009-03-16
On that Preferences screen, uncheck "Never prompt or start programs on media insertion" if the drop-down boxes are greyed out.  Then you'll be able to do one of two things:

1.  Select the appropriate application from the drop-down box.
2.  Select "Open with other Applciation..." from the drop-down box and pick your favourite apps.

If this still doesn't work, then something else is amiss here.

---

### Post by k3lt01 on 2009-03-17
Thanks orethrious for your suggestions> **orethrius said:**
> If this still doesn't work, then something else is amiss here.I think something is amiss here :( . The box you suggested is already unticked. The relevant boxes have "No Applications Found" and are greyed out .

---

### Post by sgosnell on 2009-03-17
I don't think you're in the right place.  If you are in Nautilus, you should be able to click on Edit, Preferences, and get a dialog.  On the far right tab it says "Media".  Select that tab, and you should see a list of media possibilities.  One of them is Photos.  Click on the bar, and you should see a list, "Ask what to do", "Do Nothing", "Open folder", and another choice should be "Open with Photo Manager".  The last choice will be "Open with other application", and if you click on that you can give it whatever you want.  It's the same for all the other media choices, and there are a lot of them.  You have to click on the bar, which by default I think says Ask what to do.  If you don't see this, then something is wrong in Nautilus.  The version I have is 2.25.93, which should be in the repository.

---

### Post by k3lt01 on 2009-03-18
> **sgosnell said:**
> I don't think you're in the right place. I am in the right place, trust me.

---

### Post by ugm6hr on 2009-03-18
Sounds very bizarre...

I can't find this as a bug report, which would be unusual for something so commonly used so late in the Intrepid release cycle.

Given you have found this only on your 2 installations, perhaps the problem is with your installation CD?

Are you able to use right-click: Open with... correctly?

It might be worth trying to reinstall possible problem nautilus packages:
```
sudo apt-get install --reinstall nautilus nautilus-data libnautilus-extension1 nautilus-actions 
```

---

### Post by sgosnell on 2009-03-18
That's strange.  I agree with reinstalling Nautilus.

---

### Post by k3lt01 on 2009-03-19
> **ugm6hr said:**
> Sounds very bizarre...It is indeed.

> **ugm6hr said:**
> I can't find this as a bug report, which would be unusual for something so commonly used so late in the Intrepid release cycle.I have looked around the net and couldn;t find anything either. Thats why I asked here.

> **ugm6hr said:**
> Given you have found this only on your 2 installations, perhaps the problem is with your installation CD?So should I perhaps be better off to download Intrepid again?

> **ugm6hr said:**
> Are you able to use right-click: Open with... correctly?I most certainly am.

> **ugm6hr said:**
> It might be worth trying to reinstall possible problem nautilus packages:
```
sudo apt-get install --reinstall nautilus nautilus-data libnautilus-extension1 nautilus-actions 
```Took a look in Synaptic for those files and tey were all the latest versions except for nautilus-actions which wasn't installed at all. So I installed it through Synaptic, rebooted, no change. Reinstalled the 4 files you list again through Synaptic, rebooted, no change. Re-installed from the command line, rebooted, no change.

---

### Post by ugm6hr on 2009-03-19
Afraid I have no further ideas.

I would suggest rebooting the LiveCD you installed with and run the Check CD for errors option.  Perhaps also check the md5sum.

Also - do you have the same problem with the LiveCD (i.e. no default applications)?

---

### Post by k3lt01 on 2009-03-20
I didn't use a LiveCD I used an Alternate CD because my little Acer doesn't have enough RAM to install off a Live CD. The only time I have been able to use a LiveCD was with Feisty and Gutsy.

I always check the CD for defects with every CD I use.

---

### Post by taavikko on 2009-03-20
Have tried install ubuntu desktop metapackage again

```
sudo apt-get update && sudo apt-get -f install && sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by k3lt01 on 2009-03-20
> **taavikko said:**
> Have tried install ubuntu desktop metapackage again

```
sudo apt-get update && sudo apt-get -f install && sudo apt-get --reinstall install ubuntu-desktop
```I did this as you sugested and still no change, even rebooted the machine to make sure it didn't come up after reboot.

---

### Post by taavikko on 2009-03-21
Try creating new user and login to that account, are you able to change the settings?

```
sudo adduser test
```

If everything works on test user, then some settings are b0rked on your own ~/

Then we test moving some folders to backup
```
cd; mv .local/ .config/ .gconf/ .gnome2/ -t Backup_settings/
```

You can then move carefully settings from that folder if needed.

---

### Post by k3lt01 on 2009-03-21
> **taavikko said:**
> Try creating new user and login to that account, are you able to change the settings?

```
sudo adduser test
```

If everything works on test user, then some settings are b0rked on your own ~/This worked the Media tab in the File Management Preferences has everything it should in the Test user.

> **taavikko said:**
> Then we test moving some folders to backup
```
cd; mv .local/ .config/ .gconf/ .gnome2/ -t Backup_settings/
```This didn't work unfortunately. Here's the code so you can see what happened.
```
michael@michael-laptop:~$ cd; mv .local/ .config/ .gconf/ .gnome2/ -t Backup_settings/
mv: accessing `Backup_settings/': No such file or directory
michael@michael-laptop:~$
```

> **taavikko said:**
> You can then move carefully settings from that folder if needed.I understand what you are doing, I wish I had the brains to work all this type of thing out for myself. I thank you for your help.

---

### Post by k3lt01 on 2009-03-22
I think I have done it!!!!!!!!!!!!!!!!!!!!!

About to test everything and see what happens will report back in a while what happens when I test it.

---

### Post by k3lt01 on 2009-03-22
It works yaaaaaaaaaaaaaaaaaaaaaaaaaay:popcorn:.

Thanks to everyone. After I got to copy the relevant folders, I had to change permissions to then copy the "/home/test" folders into "/home/michael". Once that was done I checked the "File Management Preferences" and they were all usable. I then checked my digital camera and Ubuntu opened F-Spot and I transfered the pictures over.

---

### Post by WIGGMPk on 2009-06-04
I am having the same problems with Jaunty amd64 installed via the alternate CD.

Gonna give this a shot tonight.

---

### Post by WIGGMPk on 2009-06-04
This is directly related to the files in ~/.local

I found that editing the Main Menu via "alacarte" can mess with things in Gnome, however I dont think it should. Let me explain.

If you open "alacarte" and than proceed to edit the Accessories menu by deleting the entry "Open CD/DVD Creator" and then open "nautilus" and go to Edit > Preferences > Preferences Tab and at the bottom, select "blank DVD disc" or "blank CD disc" the ability to select "Open CD/DVD Creator" as the default application is no longer available.

This also becomes true with other applications as well, for instance "F-Spot Photo Manager" there are two entries in the "Graphics" menu. If you delete the one that is not checked to show up, the ability to select it as a preferred application is gone, as if the system doesnt know its installed anymore. However on another user like "test", like the previous post advised to create, the ~/.local folder is new, and the menu's are unchanged, therefore the preferred applications work properly.

IMHO this is not normal activity of a system and should most likely be bugg reported as a Gnome bug because I dont think its specific to Ubuntu.

I hope im making sense, because I havent had much sleep lately lol.

:D

---

### Post by malangaman on 2010-06-11
I experienced this in Lucid 10.04 after deleting F-Spot. Once I reinstalled it the choices in Nautilus media menu were again available.

---

