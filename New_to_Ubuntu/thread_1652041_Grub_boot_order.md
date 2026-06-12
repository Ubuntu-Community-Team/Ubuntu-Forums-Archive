---
title: "Grub boot order"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Olyptic on 2010-12-24
how do i change the grub boot order to put windows on top and have it automatically boot into windows ?

---

### Post by Dovdimus Prime on 2010-12-24
I'd like to know this too. I've tried a couple of things I've found on the internet and neither of them works.

---

### Post by sffvba[e0rt on 2010-12-24
GRUB or GRUB 2?  (Easier question, which distro?)


404

---

### Post by mcduck on 2010-12-24
Check which one of the entries is the Windows one (first one is "0" for grub, second menu entry is "1" and so on).

Then edit */etc/default/grub*, and change the "GRUB_DEFAULT=0" entry to use the number for your Windows entry. So if Windows is the 3rd entry in your  Grub menu, you'd change that to "GRUB_DEFAULT=2".

Finally, run "sudo update-grub". This will read your settings and write them to Grub's configuration.

Edit:
You also wanted to move Windows to the top of the list? You can do that by renaming */etc/grub.d/30_os_prober* file. The number defines the order in which the scripts in this directory run when you run "sudo update-grub", so renaming that file to "09_os_prober" would move the Windows entry above Linux ones. And once again, run "sudo update-grub" afterwards. :)

---

### Post by Olyptic on 2010-12-24
> **not found said:**
> GRUB or GRUB 2?  (Easier question, which distro?)


404

Grub not 2 ubuntu

---

### Post by sffvba[e0rt on 2010-12-24
> **mcduck said:**
> Check which one of the entries is the Windows one (first one is "0" for grub, second menu entry is "1" and so on).

Then edit */etc/default/grub*, and change the "GRUB_DEFAULT=0" entry to use the number for your Windows entry. So if Windows is the 3rd entry in your  Grub menu, you'd change that to "GRUB_DEFAULT=2".

This would hold true for GRUB 2... as can be seen in this [thread]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+boot+order")... also note the first line of the grub file you will be editing

> # If you change this file, run 'update-grub' afterwards to update... so it seems you will have to run the following in terminal (not sure if sudo will be required):
```
update-grub
```
404

*edit: Ah! Ninja edit by mcduck :p*

---

### Post by sffvba[e0rt on 2010-12-24
> **Olyptic said:**
> Grub not 2 ubuntu

Hi Olyptic, which version of Ubuntu?  Since 9.10 Ubuntu has been using GRUB 2...


404

---

### Post by Olyptic on 2010-12-24
10.10

---

### Post by sffvba[e0rt on 2010-12-24
> **Olyptic said:**
> 10.10

Then you are using GRUB 2 and the info above is relevant :)


404

---

### Post by Olyptic on 2010-12-24
windows is last 0-6

so i change GRUB_DEFAULT=0 to GRUB_DEFAULT=6 ?

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by AlphaNeil on 2010-12-24
If you don't want to edit files then you can try StartUp-Manager.

Use following command in terminal:
sudo apt-get install startupmanager

It will provide GUI for boot options. It will make your job easy.

---

### Post by Olyptic on 2010-12-24
> **AlphaNeil said:**
> If you don't want to edit files then you can try StartUp-Manager.

Use following command in terminal:
sudo apt-get install startupmanager

It will provide GUI for boot options. It will make your job easy.

do i see th GUI at boot ?

---

### Post by amjjawad on 2010-12-24
> **Olyptic said:**
> do i see th GUI at boot ?

By default, you'll see this at booting time.

[IMG]http://ubuntuforums.org/picture.php?albumid=2140&pictureid=7149[/IMG]

---

### Post by AlphaNeil on 2010-12-24
No you wont see the GUI at boot. What I am saying it is that it provides GUI for setting boot options and you wont need to play with conf files.

Once you have installed it, go to System->Administration->StartUp-Manager.

Set the default OS and other options.

---

### Post by amjjawad on 2010-12-24
drs305 had created this great thread: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Please check it.

Also, I'd highly recommend to read more about [_**GRUB2**_]("https://help.ubuntu.com/community/Grub2").
You need to know the basics ;)

---

### Post by Olyptic on 2010-12-24
nice thanks everyone how do i mark solved

---

### Post by sffvba[e0rt on 2010-12-24
> **amjjawad said:**
> drs305 had created this great thread: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Please check it.

Also, I'd highly recommend to read more about [_**GRUB2**_]("https://help.ubuntu.com/community/Grub2").
You need to know the basics ;)

Hi, 

Thanks for the link... I just scoured drs305's other GRUB 2 thread where he deals with everything except this :p (initially thought you had linked to the same thread I had on page one, my bad)...

I concur with the sentiments that some knowledge is required to successfully use any operating system...


Regards
404

---

### Post by AlphaNeil on 2010-12-24
Glad that we could help. The option for marking thread as solved is in "Thread Tools".

---

### Post by amjjawad on 2010-12-24
> **not found said:**
> Hi, 

Thanks for the link... I just scoured drs305's other GRUB 2 thread where he deals with everything except this :p (initially thought you had linked to the same thread I had on page one, my bad)...

I concur with the sentiments that some knowledge is required to successfully use any operating system...


Regards
404

drs305 has amazing information when it comes to GRUB2.

Check "step1" in my signature. I believe this is the first step that one must do.
Yes, it's quite important to "read" about anything (not only OS) before using it :)

---

