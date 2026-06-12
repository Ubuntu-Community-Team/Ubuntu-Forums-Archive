---
title: "Rockbox &quot;could not open iPod: permission denied&quot;"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by maryalesia on 2011-01-10
Hi guys! This is an extension of a thread about mp3 players and ogg. 

Anywho, I've been trying to install rockbox on my first gen iPod nano. 

When I started the rockbox utility, I had to choose my device and mount point. I put in the correct mount and device and was then told that the mount point "cannot be written".

After some extensive googling I plugged my nano into my mom's Win7 PC and reformatted the disc to FAT32, which got me past the "cannot be written" error message.

I clicked install, and was met with "could not open iPod: permission denied".

How to I get permission?? I'm logged in as the root user & everything. :confused:

---

### Post by TechWiz2100 on 2011-01-10
From windows, open iTunes with the device plugged in and select allow disk access. I think the device's firmware is preventing you from writing data to the device, but I could be wrong.

---

### Post by maryalesia on 2011-01-10
> **TechWiz2100 said:**
> From windows, open iTunes with the device plugged in and select allow disk access. I think the device's firmware is preventing you from writing data to the device, but I could be wrong.

We don't have iTunes on a windows PC. I tried it on our iMac but there were no choices other than "restore" (because I formatted the discs). On the mac the permissions were listed as "read and write". In ubuntu they are listed as "unknown" or something to that effect. 

I tried installing rockbox through the mac but got the same results as before.

---

### Post by maryalesia on 2011-01-10
I found this answer on a rockbox forum, but it is irritatingly vague. I don't really understand what the instructions are telling me to do:

"You need to run Rockbox Utility with root permissions for bootloader installation (this is only needed for bootloader installation). Depending on your Linux setup, do the following:

- open a console. In most cases you can do this by pressing Alt-F2, then enter xterm into the dialog box that pops up.
- change to the folder you put Rockbox Utility in using the cd command.
- run Rockbox Utility using sudo with the following: sudo ./RockboxUtility"

I tried to just go and run "sudo ./RockboxUtility" but "./RockboxUtility" isn't a command, or something. 

Can anyone decipher this for me? I'm super bash-illiterate.

---

### Post by TechWiz2100 on 2011-01-10
> **maryalesia said:**
> 
I tried to just go and run "sudo ./RockboxUtility" but "./RockboxUtility" isn't a command, or something. 


you probably need to change permissions

```
chmod +x RockboxUtility

if it doesn't work try:
sudo !!
```

---

### Post by maryalesia on 2011-01-11
> **TechWiz2100 said:**
> you probably need to change permissions

```
chmod +x RockboxUtility

if it doesn't work try:
sudo !!
```

This is what I get:

```
chmod: cannot access `RockboxUtility': No such file or directory 
```

---

### Post by maryalesia on 2011-01-11
Here is what I've tried since my last post. 

I went to open RockboxUtility, but instead chose "open with other application". From there I chose "use a custom command" and typed in ```
gksu
```. 

This time the error message was "error reading partition table - possibly not an iPod". 

I'm guessing that my fix to the first problem I had (reformatting the disc to FAT32) is the cause of the problem I'm having now. 

Fiddlesticks.

---

### Post by maryalesia on 2011-01-11
I plugged my iPod into my mac mini and restored the original settings. I changed the permissions so that everyone should be able to read / write. 

Opened up rockbox using gksu again, and wasn't able to make the mount work properly. See, I created a mount called "ipod" in the terminal, but my actual iPod auto-mounts itself. So I have two mount points: "ipod" and "iPod" - the latter being the actual nano. 

The "iPod" mount point gives me an error message about the mount point not existing or something. The "ipod" mount point - the one I created in terminal - works. 

Now when I try to install I get this error message: 
Error: could not retrieve device name
:confused:

---

### Post by TechWiz2100 on 2011-01-11
the chmod command must be executed in the same directory as the Rockbox file

```
cd /path/to/file
sudo chmod +x file
```

---

