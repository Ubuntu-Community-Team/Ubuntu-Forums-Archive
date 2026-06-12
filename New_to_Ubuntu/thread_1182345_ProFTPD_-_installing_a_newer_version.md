---
title: "ProFTPD - installing a newer version"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by rmeske on 2009-06-08
I know this probably isn't the best place to post this but hopefully someone else has already solved this.

I have installed proftpd through apt-get and in doing a feat command it only returns MDTM, REST STREAM, and SIZE.

I need the ability to set the timestamp on files which seems to be supported by the mod_facts module which supports MFTM.  When looking on the ProFTPD website, this seems to be supported by ProFTPD 1..3.2 rc2 and above.  

It seems that I have 1..3.1  installed.  How would one go about installing 1..3.2 if apt-get does not get it?

Any pointers would be helpful.

---

### Post by nandemonai on 2009-06-08
> **rmeske said:**
> I know this probably isn't the best place to post this but hopefully someone else has already solved this.

I have installed proftpd through apt-get and in doing a feat command it only returns MDTM, REST STREAM, and SIZE.

I need the ability to set the timestamp on files which seems to be supported by the mod_facts module which supports MFTM.  When looking on the ProFTPD website, this seems to be supported by ProFTPD 1..3.2 rc2 and above.  

It seems that I have 1..3.1  installed.  How would one go about installing 1..3.2 if apt-get does not get it?

Any pointers would be helpful.

Remove the apt version and either find a .deb of the newer version for Ubuntu or build it from source.

---

### Post by rmeske on 2009-06-08
I am in the process of learning linux, so please point me to how to find a newer .deb version or how to build it from the source.  I have a ton of experience in the DOS, Os/2 and Windows environment, but am limited in my linux experience.  So I could use some pointers to where to find how to do this.

Thanks!

---

### Post by alphacrucis2 on 2009-06-08
> **rmeske said:**
> I am in the process of learning linux, so please point me to how to find a newer .deb version or how to build it from the source.  I have a ton of experience in the DOS, Os/2 and Windows environment, but am limited in my linux experience.  So I could use some pointers to where to find how to do this.

Thanks!

Start a the website that publish the software. If they don't provide a Debian (.deb) installer (which is what Ubuntu uses) for the release candidate. You could try downloading the source files (usually in the form of a gz compressed archive). You unpack the files and you should find a readme that tells you the instructions you need to compile the software. To compile you will probably have to install the build-essential package from synaptic if you haven't done any compiling from source before.

Actually I see that 1.3.2 official release is available from the site but isn't in either the Intrepid or Karmic repos yet. I downloaded the source gz file. Extracted and compiled ok 

On to ProFTPD site. Click on the gz link in the Current Versions Stable 1.3.2. Download the file and then double click on it and extract it wherever you like. Then open up a terminal and cd into the directory where you unpacked the files. Then:

```
sudo apt-get install build-essential
./configure
make
sudo make install
```

Some programs can be really tricky to compile and sort out the dependencies etc but this one seems straightforward.

---

### Post by nandemonai on 2009-06-09
Seems there isn't a .deb available as yet. Looks like you're going to have to install from source.

From terminal..

First, install build tools:
```
sudo apt-get install build-essential
```

Download the source:
```
wget ftp://ftp.proftpd.org/distrib/source/proftpd-1.3.2.tar.gz
```

Extract the source:
```
tar -xf proftpd-1.3.2.tar.gz
```

Enter the directory:
```
cd proftpd-1.3.2/
```

Configure the source:
```
./configure
```

Compile the program:
```
make
```

Install:
```
sudo make install
```

That's the bare bones method. It will compile and install according to the defaults laid out in the source.

I'd highly recommend reading the INSTALL file that comes in the source download to tweak anything that may need customization.

That said, I ran through a default compile and install myself and it seems to work. Haven't messed with confs or anything, just tested to make sure it builds and installs.

---

### Post by rmeske on 2009-06-09
Thank you.  That is exactly the pointers and steps I needed.

---

### Post by rmeske on 2009-06-09
Now that I have the latest version compiled and installed with the required modules for setting the timestamp of a file, the file timestamp is still not being set.  When the MFTM command is executed the server responds with Operation not permitted.

Can this be a permissions issue on the user account or on the ftp folder?  

The permissions on the ftp folder are drwxrwxr-x
The permissions on the uploaded files are -rwxrwxr-x

---

### Post by superprash2003 on 2009-06-09
you could install gproftpd , it has a GUI version , easier to install and configure

---

### Post by rmeske on 2009-06-09
Just a thought, could the permission to change the file timestamp be based on document ownership?

---

