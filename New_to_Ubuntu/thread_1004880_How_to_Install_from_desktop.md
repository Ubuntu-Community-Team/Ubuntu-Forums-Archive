---
title: "How to Install from desktop"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by onlyonesock on 2008-12-07
I have the file jre-6u11-linux-x64.bin sitting on my desktop. Please, what terminal command do I need to install it?
Thanks

---

### Post by taurus on 2008-12-07
You need to move it somewhere where you would unpack it.  /opt would be a great place so I assume that is where you want to unpack it.

```
cd ~/Desktop
sudo mv jre-6u11-linux-x64.bin /opt
cd /opt
sudo chmod 755 jre-6u11-linux-x64.bin
sudo ./jre-6u11-linux-x64.bin
```
That would create a new java directory in /opt.  Now see if you can link to it with

```
sudo update-alternatives --config java
```

---

### Post by Paqman on 2008-12-07
Installing stuff from a download is the Windows way. On Linux we use package manager to download our software straight from online repositories. What does this mean in practical terms? Open Applications > Add/Remove or System > Admin > Synaptic Package Manager and search for "sun-java6-jre" and "icedtea6-plugin", tick and hit apply to install it.

Or even easier, install ubuntu-restricted-extras, which will install both these packages, plus Flash, fonts, multimedia codecs, and a few other nice things in one step.

---

### Post by onlyonesock on 2008-12-07
Thank you taurus. I'm afraid I got

[Extracting...
./install.sfx.6808: 1: ELF: not found
./install.sfx.6808: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.]

which takes me well out of my depth. I have a 64 bit athlone and whatever I try, I can't seem to upgrade java runtime

---

### Post by onlyonesock on 2008-12-07
Thanks Paqman.
I think my problem is to do with having a 64bit machine and there being no 64 bit java for it. I saw update 11 and thought I'd have a try

---

### Post by oldos2er on 2008-12-07
> **onlyonesock said:**
> Thanks Paqman.
I think my problem is to do with having a 64bit machine and there being no 64 bit java for it. I saw update 11 and thought I'd have a try

 You can still install packages such as sun-java6-bin and sun-java6-jre using Synaptic on a 64-bit system.

---

### Post by onlyonesock on 2008-12-08
Thanks Ann
Yes I have JRE 6 through downloads manager, but I need update 10 - and now, probably, update 11. Do you know how to download and install updates 10/11 on a 64 bit please?

---

### Post by lovelyvik293 on 2008-12-08
JRE is avaliable for the 64 bit platform also.You can download it from sun site.

---

### Post by onlyonesock on 2008-12-08
Thanks Lovelyvik. That's the one I downloaded to desktop. It won't unpack

---

### Post by oldos2er on 2008-12-09
> **onlyonesock said:**
> Thanks Lovelyvik. That's the one I downloaded to desktop. It won't unpack

 You don't need to unpack a *.bin file. Open a terminal, and run these commands one at a time:

cd Desktop

chmod a+x jre-6u11-linux-x64.bin

sudo ./jre-6u11-linux-x64.bin

---

### Post by onlyonesock on 2008-12-10
Thanks Ann
This is what I'm getting (apologies for not knowing how to make a quote box)


michael@michael-desktop:~$ cd Desktop
michael@michael-desktop:~/Desktop$ chmod a+xjre-6u10-linux-x64.bin
chmod: missing operand after `a+xjre-6u10-linux-x64.bin'
Try `chmod --help' for more information.
michael@michael-desktop:~/Desktop$ 


btw, the "u10" is intentional. i lost the u11 file

---

### Post by oldos2er on 2008-12-10
> **onlyonesock said:**
> Thanks Ann
This is what I'm getting (apologies for not knowing how to make a quote box)


michael@michael-desktop:~$ cd Desktop
michael@michael-desktop:~/Desktop$ chmod a+xjre-6u10-linux-x64.bin
chmod: missing operand after `a+xjre-6u10-linux-x64.bin'
Try `chmod --help' for more information.
michael@michael-desktop:~/Desktop$ 


btw, the "u10" is intentional. i lost the u11 file

 You left out a space. Please copy and paste this command:

chmod a+x jre-6u10-linux-x64.bin

---

### Post by onlyonesock on 2008-12-10
Thanks again Ann.

Now I get this far:

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.7302: 1: ELF: not found
./install.sfx.7302: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.
michael@michael-desktop:~/Desktop$

---

### Post by oldos2er on 2008-12-10
I don't know what your problem could be, unless the file is being corrupted somehow when you download it. I just tried downloading and installing v11 of the same file, and it worked fine for me. Maybe someone else will be able to help you. Sorry.

 You did run "sudo ./jre-6u10-linux-x64.bin", right?

---

### Post by onlyonesock on 2008-12-12
Yes, did as you said. Thanks for all your help. I'll try it again with a new file

---

### Post by vandorjw on 2009-01-17
Does anyone know if there is a plugin to get it to work with firefox?

I know that in the 32 bit version there is. Just have to make a symbolic link. I have also read that using the 32 bit link works on 64 bit?

any advice would be great

Cheers - CC7

---

### Post by gtalev on 2009-01-20
> **onlyonesock said:**
> Thank you taurus. I'm afraid I got

[Extracting...
./install.sfx.6808: 1: ELF: not found
./install.sfx.6808: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.]

which takes me well out of my depth. I have a 64 bit athlone and whatever I try, I can't seem to upgrade java runtime

For everyone who hits this thread (although it is old now) - the reason that the Sun Java(tm) 32bit installer fails is because you have 64bit Ubuntu and you haven't installed 32bit-compatibility libraries. For me the following worked:

sudo apt-get -V install ia32-libs

Now the 32bit installer's executable should run fine.

---

