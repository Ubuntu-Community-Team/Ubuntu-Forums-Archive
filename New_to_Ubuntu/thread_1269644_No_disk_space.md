---
title: "No disk space"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by GiantSpider on 2009-09-18
Help I can't do anything with my ubuntu 9.04 computer. It says I have no disk space in the home directory. I can't do anything with the computer. I think it has to do with I"m dual booting. It says I have 0 bytes in the filesystem. I think I've been accidentally saving to the Ubuntu directory or something because when I shrunk the vista file system it only gave me like 6gigs or less.

    Anyways I've tried deleting stuff but it keeps saying zero bytes. I tried uninstalling programs like chess and frozen bubble and now the computer seems to be locked up, maybe you can't delete applications with zero disk space. Anyways does Ubuntu have a recycle bin function like Windows. That might explain why deleting stuff isn't helping. To make things worse it keeps trying to download a big file whenever I start firefox. Can I restart the computer or is that a bad idea when uninstalling programs?

edit:on a side note the c drive has 50 gigs free.

---

### Post by halitech on 2009-09-18
first off, how did you install Ubuntu? as a stand alone install or did you use WUBI?

Ubuntu does have a recycle bin

if you can, open a terminal and run
```
sudo apt-get autoremove
```and that will remove all the downloaded .deb files you don't need anymore.

If its locked up, do a restart and hope it starts properly.

also, post the output of
```
df -h
```

---

### Post by Jimmynemo2 on 2009-09-18
If you can, I'd install KDIRSTAT, and run that (you'll have to fix the first problem first, but once you do, it'll show you where the space is being used).

---

### Post by GiantSpider on 2009-09-18
I downloaded Ubuntu cd .iso, burned and installed.

I used the command sudo -apt-get autoremove it promted for password than said 0 upgraded, 0 newly installed 0 to remove 0 not upgraded.

I type df-h and it says, this is by hand btw since I can't post on problem computer:

/dev/sda5 Size5.8G Used5.56 Avail 0 Use%100
the last entry says /dev/sda1 size 106g used 53G avail 53G

---

### Post by t0p on 2009-09-18
You said you've deleted files.  Did you do hat in GUI, or in the terminal with the 'rm' command?

If you deleted stuff through the GUI, the deleted files are still on the computer in the wastebasket.  In the bottom right hand corner of the screen should be the wastebasket.  Right-click on it and select to empty wastebasket.  Confirm the delete and the deleted files should all be deleted permanently, releasing disk space.

In the long run you need to give ubuntu more disk space.  You said there's space available in your 'C drive'.  I take it that's in a Windows partition?  You need to use gparted to resize the Windows partition and give more space to ubuntu.

---

### Post by drs305 on 2009-09-18
Confirm this is a normal installation and not wubi?

Here are some links to guides I wrote that may help you:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by GiantSpider on 2009-09-18
Not sure how to Confirm this is a normal installation and not wubi? I tried to empty trash and its not happening. Ubuntu has been trying to uninstall the programs for over 2hrs now, it ain't happening. I'm going to risk a restart.

edit: No this is not wubi. I googled what wubi is and I'm using a dual boot. I restarted the computer but I still cannot empty the recycle bin, couldn't before either. My system is pretty locked up. I mean I can search on firefox but I can't accept any more cookies so I can't post. I'm assuming this is because there is no disc space to accept the cookies. I'm considering cutting and pasting files to a usb drive. I guess I'll use gsize to try to get more room, I needed to do that anyways. How much is good 30 gigs?

---

### Post by drs305 on 2009-09-18
The trash you may be trying to delete could be owned by 'root'. To empty it, you will need to either run the file browser as root or use terminal commands. Since the file browser is probably the safer option, run this command. It should start nautilus and open to the root trash files.

```
gksudo nautilus /root/.local/share
```
You can either browse the "Trash" folders (files and info) or just use SHIFT-DEL to remove the Trash folder and its subfolders. They will be recreated the next time you delete something as root. 

You can also browse to your own Trash folders at /home/your-username/.local/share/Trash and delete the contents, including any root trash that has accumulated there.

---

### Post by GiantSpider on 2009-09-19
> **drs305 said:**
> The trash you may be trying to delete could be owned by 'root'. To empty it, you will need to either run the file browser as root or use terminal commands. Since the file browser is probably the safer option, run this command. It should start nautilus and open to the root trash files.

```
gksudo nautilus /root/.local/share
```You can either browse the "Trash" folders (files and info) or just use SHIFT-DEL to remove the Trash folder and its subfolders. They will be recreated the next time you delete something as root. 

You can also browse to your own Trash folders at /home/your-username/.local/share/Trash and delete the contents, including any root trash that has accumulated there.

I tried browsing to my trash. I went home/username and then I saw no local folder in my home directory.

I tried the command and it said no such file or directory in an error. In terminal it gave an error also: ** (nautilus:7741 : Warning **: Unable to add monitor and more I'm typing this by hand and lazy :)

---

### Post by Elfy on 2009-09-19
> I tried browsing to my trash. I went home/username and then I saw no local folder in my home directory.It is a hidden folder - do Ctrl+H - the folder will be .local

---

### Post by GiantSpider on 2009-09-19
Alright well I'm getting tired I'll try the hidden folders tommorow. When I get tired I type random things in.

 I tried install gparted on a usb drive but when I tried running Live USB helper I got an error about languages I downloaded that. Then I got the error about the missing .dll. I downloaded it and put it in c -> windows -> system32. This is in Vista btw.

 I tried running again and now it gave the error again. Finally I typed in the cmd in the faq, regsvr32 and it says this version isn't compatible with a 64-bit system or the likes. 

"the module is may not be compatible the version of windows you are running" I freakin am started to hate Vista this is the reason I'm trying to switch to Ubuntu and now Vista doesn't want to let go lol.

---

### Post by drs305 on 2009-09-19
> **GiantSpider said:**
> I tried browsing to my trash. I went home/username and then I saw no local folder in my home directory.

I tried the command and it said no such file or directory in an error. In terminal it gave an error also: ** (nautilus:7741 : Warning **: Unable to add monitor and more I'm typing this by hand and lazy :)

Do you have hidden folders viewable? The . in front of "local" means local is a hidden folder. Go to your home directory and press CTRL-H to view hidden folders if you can't see them.

For root nautilus, try
```

gksu nautilus

```
You will still get error messages in the terminal but nautilus should open regardless.

---

### Post by GiantSpider on 2009-09-19
oh wow thanks I did the delete trash and I got an error saying cannot put in trash:invalid argument I deleted and got 536 mbs. Now I need need a bigger partition or to be saving to a different filesystem.

Crap as soon as I got discspace firefox resumed downloading the file and now I'm out again. It was a 1 gig file. Ok I think I fixed it I hit cancel download which didn't work before when I had no disc space.

---

### Post by GiantSpider on 2009-09-19
I used unetbootin with a gparted .iso and a usb drive. Having trouble booting via the usb drive. I have the same problem with another usb drive that used unetbootin for ubuntu 9.04. Any suggestions?

---

### Post by GiantSpider on 2009-09-19
I tried gparted on another computer, xp, and it was able to boot via the usb drive. So not sure why some computers would reject gparted and others not. Would the usb startup disk creator work better than unetbootin if the usb flash drive doesn't work on a computer?

---

### Post by GiantSpider on 2009-09-20
Figured it out using good old google. First match on search results. I have to use f12 for boot menu then select hdd which has a + next to it which means theres two hdd then I select the usb! I didn't think of my usb as a hdd lol.

---

