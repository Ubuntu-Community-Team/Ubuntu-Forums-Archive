---
title: "bible desktop"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by menschtx on 2008-12-24
I read and tried changing the permissions for the BD, I also right clicked the BibleDesktop.exe and selected "open with redwine app" and nothing happens. Tried the listing papa-san wrote, I removed /tmp from the cmd line and am unable to,  get:
-desktop:~$ cd /jsword-1.0.7$ ./BibleDesktop.sh
bash: cd: /jsword-1.0.7$: No such file or directory // also checked out;Try `install --help' for more information, and followed the install step, still nada.
One thing the only place I can find permissions is in the download before extraction, I have tried read only and read and write, and still nothing after extracting.
Thanks for your help

---

### Post by jerome1232 on 2008-12-24
> **menschtx said:**
> I read and tried changing the permissions for the BD, I also right clicked the BibleDesktop.exe and selected "open with redwine app" and nothing happens. Tried the listing papa-san wrote, I removed /tmp from the cmd line and am unable to,  get:
-desktop:~$ cd /jsword-1.0.7$ ./BibleDesktop.sh
bash: cd: /jsword-1.0.7$: No such file or directory // also checked out;Try `install --help' for more information, and followed the install step, still nada.
One thing the only place I can find permissions is in the download before extraction, I have tried read only and read and write, and still nothing after extracting.
Thanks for your help

First your talking about a .exe then your talking about what looks to be a shell script which one is it?

If it's a .exe then try running it like this
```
wine /path/to/windows/executable
```

if it's a linux binary or shell script then try this
```
chmod +x /path/to/binary/file
sh /path/to/binary/file
```

It may want root access to install in that case:
```
 sudo chmod +x /path/to/binary
sudo /path/to/binary/file
```

---

### Post by menschtx on 2008-12-27
jerome1232, 
thanks for your response, I tried to use wine but no action. I searched for another - "gnomesword-2.4.1.tar.gz" and will try this. In searching forums, I found that .exe doesnt work very well with linux ubuntu, what would be the alternative? 
Once again thank you

---

### Post by jerome1232 on 2008-12-27
Well yeah .exe would be a Windows Executable!!! You know gnomesword version 2.2.3 is available in the Ubuntu repo's. You can use synaptic to install it. (System->Administration->Synaptic Package Manager)

or from the command line

```
sudo apt-get install gnomesword
```

Now if you really need the newest version (I'm not sure which version they have) you can add their repository. Instructions are [here]("http://gnomesword.sourceforge.net/debian.php") but I'll tell you exactly how to add it.

System->Administration->Software Sources, click on Third Party Software, click add; then add the line below, click add source, close, reload.

```
deb http://dominique.corbex.net/gnomesword/ubuntu intrepid main
```


Now you can use synaptic to install their newest version or once again from the command line you can use apt-get

```
sudo apt-get install gnomesword
```

---

### Post by richardneish on 2009-11-23
These instructions are written for BibleDesktop 1.6 and Ubuntu 9.10 running XFCE.  It should still work with other versions with minor changes. 

To get BibleDesktop installed and configured with Ubuntu:

Download the latest version of BibleDesktop for Linux from
[http://www.crosswire.org/ftpmirror/pub/jsword/release/bibledesktop-latest-bin.tar.gz](http://www.crosswire.org/ftpmirror/pub/jsword/release/bibledesktop-latest-bin.tar.gz)
(save this file as /tmp/bibledesktop-latest-bin.tar.gz)

Open a terminal (Applications -> Accessories -> Terminal)

In the terminal, type the following commands:
  ```

cd /usr/local
sudo tar xvzf /tmp/bibledesktop-latest-bin.tar.gz

```This should have unpacked the BibleDesktop files to /usr/local/jsword-1.6/

From the terminal test that it's working by running the command:
  ```
/usr/local/jsword-1.6/BibleDesktop.sh
```After a few seconds, you should see BibleDesktop running.  Close it down now and let's create an entry in the menu to run this.

Run the menu editor (System -> Preferences -> Main Menu) and add an entry for BibleDesktop.  I put it under the "Other" category, but that's up to you.

---

