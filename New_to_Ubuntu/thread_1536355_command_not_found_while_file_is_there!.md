---
title: "command not found while file is there!?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by mohico on 2010-07-22
Hi 

I'm trying to install MATLAB here. I tried to install directly from the GUI file browser but couldn't as didn't have permission (folder is not writeable!)

Then I turned to the terminal to use the SUDO command - however, I keep on getting on getting "sudo: ./install: command not found" when executing

```

sudo ./install

```I'm trying this from the mounted ISO directory and sure that it has the file "install" (can be found by ls - and also the same one that I ran from the GUI).

Any comments are welcome.

Best
M

---

### Post by lisati on 2010-07-22
Are you running it from the folder which contains the file?

---

### Post by mohico on 2010-07-22
> **lisati said:**
> Are you running it from the folder which contains the file?

100% and that why it's surprising!

---

### Post by mcduck on 2010-07-22
Does the file have execute permission enabled?

```
chmod +x install
```


edit:

Now that I read your post again, the problem is indeed the lack of execute permission, but it's a bit more complicated than that. You are trying to do this directly from a mounted .iso image, while the ISO9660 file system doesn't even have support for such permissions. So you *can't* enable it.

You have two alternatives:

1.copy all stuff to the Linux drive, where you'll be able to set the file as executable.

2. If the "install" file is actually a shell script (instead of executable binary file, for example), you can use "sudo sh install", which will work even without the execute permission since you aren't executing the file, you are executing the shell and the file name is just a parameter to the command...

---

### Post by mohico on 2010-07-22
> 

You have two alternatives:

1.copy all stuff to the Linux drive, where you'll be able to set the file as executable.

2. If the "install" file is actually a shell script (instead of executable binary file, for example), you can use "sudo sh install", which will work even without the execute permission since you aren't executing the file, you are executing the shell and the file name is just a parameter to the command...I'm keen on getting it working directly from the iso image to get the know-how for the future. However, executing 
```

sudo sh install

```returns 
sh: Can't open install

By the way, as I mentioned before, he file does run from the GUI. I just didn't know how to run it with permissions from there (at one stage in the installation wizard, it complains of the installation folder being not writeable)

M

---

### Post by mohico on 2010-07-22
Update: I also tried switching to root by "sudo su" and gave me on this occasion "Permission denied"

---

### Post by mohico on 2010-07-22
So now it's working! It seems that I had some problems in the AcetoneISO - the programme I used for mounting the CD. Doesn't make sense to me, ah well.

---

### Post by mcduck on 2010-07-22
You don't need any additional programs to mount an .iso image. Just right-click the image and select "Open with Archive Mounter". ;)

(this works on 10.04, in older Ubuntu versions you might need to mount the .iso from command-line)

---

### Post by aliemim on 2010-12-30
Greatings to all, 
while it worked like a charm in 10.04, I am having a similar problem on a fresh install of Ubuntu 10.10. When I try to run "install" from the command line in an extracted-iso folder via:
```
sudo ./install
```
it gives the same message "sudo: ./install: command not found", as in previous posts. I tried changing the mode with "chmod 777 install.sh" and then I get message: 
 
"Sorry! Could not determine the Format of the CDROM for architecture (glnx86)"
 
Anybody to help "this year"?

---

