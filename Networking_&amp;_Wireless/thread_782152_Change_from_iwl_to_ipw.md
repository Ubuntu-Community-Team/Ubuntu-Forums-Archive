---
title: "Change from iwl to ipw"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by lnogueir on 2008-05-04
Hi!

Is there any way to install ipw3945 driver on Hardy and remove iwl driver?

Ipw works a lot better...

Can someone do a How-to?

Thanks!

---

### Post by pjfl on 2008-05-04
Try this [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html). Please post back and lets us know if it works

---

### Post by lnogueir on 2008-05-05
Hi! Thanks for the help!

I aplly the patch but I keep getting a lot of errors when trying to compile ipw driver.

I'm a newbie at this things of compiling!

If someone can help-me I will appreciate.

Thank you!

---

### Post by lnogueir on 2008-05-14
[http://www.klamstwo.org/evad/archives/59](http://www.klamstwo.org/evad/archives/59)

At the end of this page there is a How-to... Can someone build a How-to to ubuntu Hardy!

Please! I loose my internet connection every 10 minutes!

---

### Post by digitalvectorz on 2008-09-28
A little late, but I'll share what I did to go from iwl3945 to ipw3945 [on Hardy].  NOTE: This walk through is going to make heavy use of the command line interface.  

***We are going to assume that the files to download are being saved to 
~/Desktop/

**1.**  Download ipw3945 microcode from [http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz](http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz)

**2.**  Extract the contents of that file into a folder on the desktop.  Then we're going to copy the file (ipw3945.ucode) into /lib/firmware/`uname -r` .  In the terminal, type:
```

cd ~/Desktop
tar zxvf ipw3945-ucode-1.14.2.tgz
cd ipw3945-ucode-1.14.2/
sudo cp ipw3945.ucode /lib/firmware/`uname -r`/

```

**3.**  Download the regulatory daemon from [http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz](http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz)

**4.**  Now we're going to extract the file's contents and copy the necessary files over:
```

cd ~/Desktop
tar zxvf ipw3945-1.7.22.tgz
cd ~/Desktop/ipw3945d-1.7.22/
sudo cp ipw3945d-st* /sbin/

```
If you're running a 32-bit processor
```

sudo cp x86/ipw3945d /sbin/

```
If you're running a 64-bit processor
```

sudo cp x86_64/ipw3945d /sbin/

```

**5.**  Download the ipw3945 source code from [http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.2.tgz](http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.2.tgz)

**6.**  Now extract those files
```

cd ~/Desktop
tar zxvf ipw3945-1.2.2.tgz
cd ipw3945-1.2.2/

```

**7.**  Download the patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html) (Right Click > Save Link As > Choose Desktop/ipw3945-1.2.2 > Save)

**8.**  Apply the patch.
```

patch -p1 < ipw3945.patch

```
You'll probably get an error similar to this:
missing header for unified diff at line 3 of patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
File to patch: 

When you see File to patch: ,  enter the filename ipw3945.h as follows
```

File to patch: ipw3945.h

```

**9.**  Make and Make Install
```

sudo make && sudo make install

```

**10.**  Edit /etc/modprobe.d/ipw3945 (create if it doesn't exist)
```

sudo gedit /etc/modprobe.d/ipw3945

```
Add the following lines
```

install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d --quiet
remove ipw3945 /sbin/ipw3945d --kill ; /sbin/modprobe -r --ignore-remove ipw3945

```
Save.

**11.**  Edit /etc/modprobe.d/blacklist
```

sudo gedit /etc/modprobe.d/blacklist

```
Add the following to the end of the file
```

# blacklist iwl3945 wireless driver
blacklist iwl3945

```

**12.**  Restart.  And There you go.

These are the steps I took.  Hope this helps.

NOTE:  If for some reason your wireless doesn't work, just edit /etc/modprobe.d/blacklist and change the last line you added:
```

blacklist iwl3945

TO

#blacklist iwl3945

```

and change /etc/modprobe.d/ipw3945 :
```

#install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d --quiet
#remove ipw3945 /sbin/ipw3945d --kill ; /sbin/modprobe -r --ignore-remove ipw3945

```

Then restart.  You should have you're old wireless driver in operation again.

---

