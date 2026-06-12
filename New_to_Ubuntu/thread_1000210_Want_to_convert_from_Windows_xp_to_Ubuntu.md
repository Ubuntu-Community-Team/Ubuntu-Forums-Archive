---
title: "Want to convert from Windows xp to Ubuntu"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by dgerwin11 on 2008-12-02
I have an old windows xp machine that I want to convert to Xubuntu or Ubuntu.  when I try installing the disc (both act the same), the system freezes before I can  install.  I suspect there is a lot of crud on hd that is taking up too much space.  Ihave one computer with Ubuntu 8.10 as only os and one with Xubuntu 8.10 as only os.  There are problems with Xubuntu machine.  I would like to take one of my old computers, totally remove all traces of Windows and run it with one of the buntu's.  How to get rid of windows if I don't have ubuntu installed?

For my computing needs, Windows of any flavor is not needed or wanted.  I've only used Ubuntu for a couple months and I won't look back.

Thanks

---

### Post by dondad on 2008-12-02
> **dgerwin11 said:**
> I have an old windows xp machine that I want to convert to Xubuntu or Ubuntu.  when I try installing the disc (both act the same), the system freezes before I can  install.  I suspect there is a lot of crud on hd that is taking up too much space.  Ihave one computer with Ubuntu 8.10 as only os and one with Xubuntu 8.10 as only os.  There are problems with Xubuntu machine.  I would like to take one of my old computers, totally remove all traces of Windows and run it with one of the buntu's.  How to get rid of windows if I don't have ubuntu installed?

For my computing needs, Windows of any flavor is not needed or wanted.  I've only used Ubuntu for a couple months and I won't look back.

Thanks

Will it boot up and run from the Ubuntu CD? If so, then I would just use gparted , set up three partitions, and format all of them as linux. That will clear all of the junk on the drive. Three partitions, one for /, one for /home, and one for swap. Sizes dependent on the size of the hard drive.

If it won't boot from the CD, then there are other issues that may have to be addressed. Post the errors you get if it does not boot.

---

### Post by icarid_17 on 2008-12-02
> **dgerwin11 said:**
> I have an old windows xp machine that I want to convert to Xubuntu or Ubuntu.  when I try installing the disc (both act the same), the system freezes before I can  install.  I suspect there is a lot of crud on hd that is taking up too much space.  Ihave one computer with Ubuntu 8.10 as only os and one with Xubuntu 8.10 as only os.  There are problems with Xubuntu machine.  I would like to take one of my old computers, totally remove all traces of Windows and run it with one of the buntu's.  How to get rid of windows if I don't have ubuntu installed?

For my computing needs, Windows of any flavor is not needed or wanted.  I've only used Ubuntu for a couple months and I won't look back.

Thanks

all right, so the easiest way to format your hard drive is as follows:
step 1. get a live cd, I suggest ubuntu (at least 7.10, anything before that might not have gparted (not positive though)) because i know it has gparted
step 2. Boot the cd, it should boot automatically if its in the cd drive when the computer starts up, if it doesn't then you will need to press the button for the boot menu, which should show up somewhere on the screen just before booting.
step 3. select your language of choice from the menu that pops up 
step 4. press enter (the cursor should already be on try or install ubuntu)
step 5. go to system > administration > partition editor
step 6. select the drive you want, right click it
step 7. if the format option is greyed out, then click unmount
step 8. right click the unmounted partition and click delete
step 9. click apply, you've probably already seen it, though if you haven't because of something bizzare, like it being somehow obscured because, in some impossible seeming manner the window got moved too far up so everything above the big yellow bit showing how much space you have can't be seen then its just above the big yellow thing, if my scenario actually somehow happened and you can't move the window then just hold alt and click-drag the window to wherever is more comfortable.  

I included a lot of steps because it makes everything easier for me to say in a clear, concise (well, maybe just kinda-sorta concise)manner
I'll make another post with steps on how to partition your hard drive, (especially to be clear on the swap thing, because making a new swap can be a pain if you try to find swap in the list of mount points like I did once)

---

### Post by Sef on 2008-12-02
Read [Psychocats]("http://psychocats.net/ubuntu").

What are your system specs?

---

### Post by manuleka on 2008-12-02
it could be driver issues (maybe video)... have you tried installing with text-based? try downloading the alternate installation cd from here 

64bit: [http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-amd64.iso.torrent)
32bit: [http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent)

i have had the same problem which got todo with my video card X600

but yours could be anything else...

---

### Post by Gannon8 on 2008-12-02
I had this problem before. It has nothing to do with your HDD.
Heres the steps to solve it, assuming you do not need ANYthing on windows now (INCLUDING MY DOCUMENTS!):
1. Boot the LiveCD
2. Go to System > Administration > Partition Editor
3. Right click on the giant green bar with a hollow white part and select delete
4. Right click on the grey part and select "new"
5. Select linux-swap from the File System drop-down menu
6. Type 1000 into the size box
7. Drag the red bar on the top of the screen all the way to the right
8. Click "Add"
WARNING! NEXT STEP IS POINT OF NO RETURN!
9. Click "Apply"
10. Wait
11. Reboot into the liveCD
12. Try it again

---

### Post by seshomaru samma on 2008-12-02
if the specs are low a live CD will not run
if you want to create a very slim install then use the Ubuntu Server install. You will get a command line system.
Then run this command :
```
sudo aptitude install firefox xfce4 thunar xterm xorg xdm
```
you can then slowly add apps as you need.
Psychocats has a more detailed explanation

---

### Post by icarid_17 on 2008-12-02
i know that i said i would post about partitions, but i realized that if the hard drive is empty you can just click install, which is on the desktop. on a side note, your computer could just not be powerful enough, i suggest using something with the xfce desktop (like xubuntu, or if you choose it (xfce as opposed to kde or gnome) during the installation, fedora)

---

### Post by dgerwin11 on 2008-12-03
Thanks all,

I now have 2 computers running on ubuntu 8.10 flawlessly.  In other words I am now a Windowless household.

While I am still learning how to handle Ubuntu, I find it far superior to Windows.  I will never buy another Windows machine.

---

