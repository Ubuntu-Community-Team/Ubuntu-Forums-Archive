---
title: "No wired internet connection after clean install Ubuntu 16.04"
date: 2018-03-11
forum: Networking &amp; Wireless
---

### Post by ithen9390swn30 on 2018-03-11
I'm having a strange network issue after a fresh install of Ubuntu 16.04 on a HP ProBook 4540s laptop. I can connect by Wifi just fine but on wired it rarely can make a connection. Pinging the router fails (destination host unreachable) and pinging my Windows laptop also fails with similar results. I can see the HP laptop when I log into the router and I see nothing out of the ordinary. Using Wifi only isn't an option because the signal is too weak in my room and I have to go downstairs to get a good signal.

I've searched around for issues similar without results (most involve wireless connection). I did ran the [wireless script]("https://ubuntuforums.org/showthread.php?t=370108") and the pastebin link of the results is;
[https://paste.ubuntu.com/p/KzRFDc3dJd/](https://paste.ubuntu.com/p/KzRFDc3dJd/)

However, in a very rare case the wired connection is created very swiftly and the internet connection remains stable and fast (or as fast as it can get here) until I log out or the computer goes into stand-by. In this scenario pinging the router works but pinging my Windows laptop fails still. I've updated Ubuntu (sudo get-apt upgrade) several times during the rare occassions that it has connection. The pastebin link above was ran when the connection worked.

Warning = This is my first encounter with Ubuntu so I'm still a newbie in this world.

---

### Post by praseodym on 2018-03-11
Change the driver from r8169 to r8168:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-1_all.deb
sudo dpkg -i r8168-dkms_8.045.08-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by ithen9390swn30 on 2018-03-11
I'm getting a 404 error on that second command. Should it be "[r8168-dkms_8.045.08-2_all.deb]("http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-2_all.deb")"?

---

### Post by praseodym on 2018-03-11
Yes!

```
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-2_all.deb
sudo dpkg -i r8168-dkms_8.045.08-2_all.deb
```

---

### Post by ithen9390swn30 on 2018-03-11
Kapow! It worked! Thank you!

---

