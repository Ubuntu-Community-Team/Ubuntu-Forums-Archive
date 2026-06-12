---
title: "Installing Java"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by fabis94 on 2010-02-06
Ok i tried to install Java and the installation failed. Can anyone tell me what's wrong?

```
Do you agree to the above license terms? [yes or no]
yes          
Unpacking...
/home/fabis/Desktop/jre-6u18-linux-i586.bin: 336: cannot create install.sfx.3939: Permission denied
Checksumming...
/usr/bin/sum: install.sfx.3939: No such file or directory
[: 363: -ne: unexpected operator
[: 363: -ne: unexpected operator
chmod: cannot access `install.sfx.3939': No such file or directory
Extracting...
/home/fabis/Desktop/jre-6u18-linux-i586.bin: 366: ./install.sfx.3939: not found
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

```

---

### Post by Temposs on 2010-02-06
You can install java from the ubuntu repositories(like most apps), so there's no need to download it yourself. In fact, there are a lot of useful things, including Java, that could be installed if you install the "ubuntu restricted extras" package. Just go to the Software Center and search "ubuntu restricted extras". It will install Java for you, as well as a lot of other nice stuff you'll need.

---

### Post by fabis94 on 2010-02-06
Okay thanks. Could i still know what was wrong in that installation?

---

### Post by Temposs on 2010-02-06
you needed to put a "sudo" at the beginning of your command, I think.

In the future, always check to see if Ubuntu has put the app you need in the Software Center or Synaptic Package Manager before installing from a website download. This will help preserve your system's stability and security :-)

---

### Post by *Raz0r* on 2010-02-06
you can just type in the terminal sudo apt-get install jdk this will install everything, the general enviroment and development kit.

---

### Post by fabis94 on 2010-02-06
Yes, but i think it installs the older version. I need the most up-to-date Java. Is there a way to install that without messing with the CLI?

---

