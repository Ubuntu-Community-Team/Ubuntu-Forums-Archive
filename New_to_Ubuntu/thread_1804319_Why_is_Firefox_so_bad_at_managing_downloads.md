---
title: "Why is Firefox so bad at managing downloads?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-14
I was downloading three files in firefox a few minutes ago, and now when I check the status, it's stuck at 30%. The green bars are no longer moving and it says 0 of 0MB at 0KB/s. When I right click pause and then resume, it says the files can no longer be saved and are automatically cancelled.

Why does this keep happening?

Am I supposed to use a download manager to fix this? Is there anyway to fix this without having to install a download manager?

---

### Post by hakermania on 2011-07-14
Well this happens to me occasionally but it is the server who sends the file the one to blame rather than the firefox.
You can alternatively use
```

wget http://link/to/file

```
if possible. This will be an option if you don't want to install a download manager.

---

### Post by brawnypandora0 on 2011-07-14
What server? You mean my Service Provider has bad equipment?

---

### Post by amjjawad on 2011-07-14
I don't think it has to do with Firefox itself.

I have had this issue with almost all the browsers I have used. Perhaps it has to do with your internet speed, the server you are downloading from, etc.

Download Managers could be useful but for me, I don't need any as long as I know what I'm doing. For large files, I use Torrent Programs (utorrent in Windows and Transmission in Linux).

I had that problem when my Internet Speed was 30KB/sec. Now, it's 100KB/sec. I don't have that problem anymore.

---

### Post by brawnypandora0 on 2011-07-14
How do I upgrade to a better server?

---

### Post by amjjawad on 2011-07-14
> **brawnypandora0 said:**
> How do I upgrade to a better server?

What do you mean a better server?
You mean another ISP? or upgrade your Internet Speed?

---

### Post by philinux on 2011-07-14
> **brawnypandora0 said:**
> How do I upgrade to a better server?

They mean the server where the file you want resides. You can't do anything about that. Unless its hosted somewhere else.

---

### Post by I2k4 on 2011-07-14
Actually one of the few ways I find FF is better than Chrome on Ubuntu is handling installation of .deb packages.  With FF, if there is a good .deb package, it will handle the install during the download.  With Chrome you're limited to downloading to directory and left to fool around with the package in Ubuntu. Whenever I'm looking for software that's not in the Synaptic PM, I use FF.

---

### Post by brawnypandora0 on 2011-07-14
> **hakermania said:**
> Well this happens to me occasionally but it is the server who sends the file the one to blame rather than the firefox.
You can alternatively use
```

wget http://link/to/file

```if possible. This will be an option if you don't want to install a download manager.

not working

$ wget [http://link/to/file](http://link/to/file)
--2011-07-14 15:24:14--  [http://link/to/file](http://link/to/file)
Resolving link... failed: Name or service not known.
wget: unable to resolve host address `link

---

### Post by ajgreeny on 2011-07-14
So that proves it's not FF at fault but your web connection.

---

### Post by dFlyer on 2011-07-14
I've never had a problem downloading any files/programs/iso using firefox.

---

### Post by 3rdalbum on 2011-07-15
> **brawnypandora0 said:**
> not working

$ wget [http://link/to/file](http://link/to/file)
--2011-07-14 15:24:14--  [http://link/to/file](http://link/to/file)
Resolving link... failed: Name or service not known.
wget: unable to resolve host address `link

When they say "use wget link/to/file", they mean that you should subsitute "link/to/file" for whatever the URL is of the file you want to download.

Your original problem actually sounds more like you're using mobile broadband. Mobile broadband uses the mobile phone towers to give you an internet connection, and unfortunately it's quite unreliable for downloading big files unless you're very near to the tower.

---

### Post by brawnypandora0 on 2011-07-15
I'm using wired cable. What makes you think I'm using mobile?

---

### Post by 3rdalbum on 2011-07-15
> **brawnypandora0 said:**
> I'm using wired cable. What makes you think I'm using mobile?

Mobile broadband connections often do what you reported in your original post.

---

### Post by amjjawad on 2011-07-15
> **brawnypandora0 said:**
> I'm using wired cable. 

What is your Internet Speed???

What is(are) the size(s) of the files(s) you are trying to download?


Please note that you need to mention more details whenever you post. We are trying to help based on what YOU posted. We don't know what kind of connection or internet speed you do have unless YOU tell us :)

---

### Post by SavageWolf on 2011-07-15
Does this happen when you download all files? And what are you downloading?

---

### Post by androssofer on 2011-07-15
get the add-on downthemall, works a treat for me :-)

---

### Post by lovinglinux on 2011-07-15
> **androssofer said:**
> get the add-on downthemall, works a treat for me :-)

+1

I don't have stability issues with Firefox download manager, but speed is considerably slow when compared to [DownThemAll]("https://addons.mozilla.org/en-US/firefox/addon/201/").

---

### Post by brawnypandora0 on 2011-07-16
> **amjjawad said:**
> What is your Internet Speed???

What is(are) the size(s) of the files(s) you are trying to download?


Please note that you need to mention more details whenever you post. We are trying to help based on what YOU posted. We don't know what kind of connection or internet speed you do have unless YOU tell us :)

The files are around 700MB. 

How do I find out my Internet Speed?

---

### Post by amjjawad on 2011-07-16
> **brawnypandora0 said:**
> How do I find out my Internet Speed?

Two simple ways to find out:

1- Whenever you download, check the download rate. How many KB per second? It's on the download small window.

2- Call your ISP and ask them about your subscription. 


That's all :)

---

### Post by brawnypandora0 on 2011-07-18
Isn't there another way instead of downloading or phoning to find out what my speed is?

My harddrive is maxed out and I don't have their phone number.

---

### Post by brawnypandora0 on 2011-07-19
Ok got another download:

it says 150 KB/s but is fluctuating up and down.

Does this mean I have broadband?

---

### Post by amjjawad on 2011-07-19
> **brawnypandora0 said:**
> Ok got another download:

it says 150 KB/s but is fluctuating up and down.

Does this mean I have broadband?

Not sure what type of connection but it looks like 2Mbps.
Mine is 1Mbps and the average speed of download is 100KB/sec.

It's not very slow. I still think the problem is NOT with Firefox.
With such connection, don't expect to download 3 files at the same time and each file is more than 300MB for example.

I use Torrent for Windows and Transmission for Ubuntu when I need to download large files.

---

### Post by androssofer on 2011-07-19
> Isn't there another way instead of downloading or phoning to find out what my speed is?

My harddrive is maxed out and I don't have their phone number. 


i use this to make sure my isp aint slacking off...

[http://www.broadbandspeedchecker.co.uk/](http://www.broadbandspeedchecker.co.uk/)

should give you a close enuf estimate to ur interwebz speed and u dont hav to download or ring up :-)

---

### Post by jtarin on 2011-07-19
> **brawnypandora0 said:**
> Isn't there another way instead of downloading or phoning to find out what my speed is?

My harddrive is maxed out and I don't have their phone number.
[http://www.speedtest.net/](http://www.speedtest.net/)

---

