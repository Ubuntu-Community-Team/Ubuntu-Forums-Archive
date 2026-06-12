---
title: "New to linux - Need some help"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Jasonb61 on 2010-05-29
Hey everyone! My name is Jason, i'm 22, and just completed my CarPC build. I decided to install a version of linux because I've always heard good things and wanted an excuse to switch.

Minimal load time is a top priority in this computer so was Ubuntu a good choice? Any tips to maybe cut the load time (which is pretty fast anyways)

I am also having trouble playing Mp3 files as I do not have the codecs on the computer. Can someone give me pretty straight forward advice on how to get this taken care of? I do not have internet on the computer at this time.

Any other tips, suggestions, or information useful to a Windows user is greatly appreciated.

Thanks!

---

### Post by atomizer on 2010-05-29
For installing codec, you could use the[ medibuntu reposetories]("https://help.ubuntu.com/community/Medibuntu").

I would advice to connect to internet for the installation, else you have to look for .deb packages on another pc and pray that dependencies are satisfied.

---

### Post by -humanaut- on 2010-05-29
Download these to a either a CD or USB stick and it will install all the necessary codecs [http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

and in regards to boot time I think its pretty universal across all the distributions right now anywhere from 10-25 seconds which is a far-cry better then Mac or Windows.

---

### Post by Jasonb61 on 2010-05-29
> **-humanaut- said:**
> Download these to a either a CD or USB stick and it will install all the necessary codecs [http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

and in regards to boot time I think its pretty universal across all the distributions right now anywhere from 10-25 seconds which is a far-cry better then Mac or Windows.

I went there and downloaded some packages but it kept wanting me to download more and more because I kept getting various dependency errors.

Now I had to download libc6 and I did. When trying to install it, it says "Breaks existing package 'Mountall' dependency libc6 (<2.11)

I dunno what I did wrong but I've never had to go through so much just to get some Mp3 files to play......

---

### Post by daimaru on 2010-05-29
it would be far easier if you could just go online with your computer for once. then you could at least get all the needed codecs etc.. if that is not possible at all ( why not , does it not have any network card ? ) you can still install the ubuntu-restricted-extras (or someting like that || got to search for it in synaptic ) then at least you should have all the flash mp3 stuff working . for full video codec support you should install the medibuntu.org w32 or w64 codecs and libdvd stuff. Just read the stuff on medibuntu.org

---

### Post by Jasonb61 on 2010-05-29
> **daimaru said:**
> it would be far easier if you could just go online with your computer for once. then you could at least get all the needed codecs etc.. if that is not possible at all ( why not , does it not have any network card ? ) you can still install the ubuntu-restricted-extras (or someting like that || got to search for it in synaptic ) then at least you should have all the flash mp3 stuff working . for full video codec support you should install the medibuntu.org w32 or w64 codecs and libdvd stuff. Just read the stuff on medibuntu.org

It doesn't have a wireless adapter and so with it being a CarPC, I can't really use a network cable unless I disconnected everything and brought it inside lol I was so focused on the multimedia accessories, that I overlooked a simple wireless adapter. I ordered one yesterday so I suppose I will wait until it arrives. I'm just a little impatient lol

---

### Post by daimaru on 2010-05-29
hi jason sorry kindof did not get the fact that your actually using a pc in ur car ... CarPC . ^.^ well did you try installing restricted extras from cd ? sorry not to up to date on installing stuff from removable media. sorry, but i guess you can somehow get the needed packages onto a external drive. but how to satisfy all dependancies.. i do not know. some ubuntu geek will probably jump in right about now :)

---

### Post by Jasonb61 on 2010-05-29
> **daimaru said:**
> hi jason sorry kindof did not get the fact that your actually using a pc in ur car ... CarPC . ^.^ well did you try installing restricted extras from cd ? sorry not to up to date on installing stuff from removable media. sorry, but i guess you can somehow get the needed packages onto a external drive. but how to satisfy all dependancies.. i do not know. some ubuntu geek will probably jump in right about now :)

It's fine. I am not always clear =) If there is a way, I am willing to hear. However, I have a wireless adapter coming soon so I may just have to wait. I was just being impatient and wanted to get everything playing. A few more days won't hurt I suppose.

---

### Post by Jasonb61 on 2010-06-09
Getting ready to switch back to Windows... For some reason I cannot connect to my wireless network at home. It keeps prompting me for the WEP Key and I KNOW I've entered it correctly each time. The WEP key is set to the default setting that came on the router and none of the other computers in the house are having connection issues. Including this one. It's an Open-type encryption according to the manual. Any suggestions before I wipe the disk clean and start over?

---

### Post by anewguy on 2010-06-09
A dumb question, but is it really asking for the network password, or is it asking for the keyring password to unlock the network?

Dave ;)

---

### Post by Adan1900 on 2010-06-10
Hy Jason.
Please go to System&#8594;Preferences&#8594;Network Connections&#8594;Wireless&#8594;select your wireless connection&#8594;Edit
Look at the top of the pannel. "connect automatically" should be selected. Look at the bottom of the pannel. Connection should be "Available to all users". Than go to Wireless Security. The WEP should be entered there.Apply
reboot

---

### Post by Jasonb61 on 2010-06-10
Tried this already with no luck. Never had this happen with Windows... Cannot even accomplish simple tasks with ubuntu

---

### Post by Adan1900 on 2010-06-11
In one case the problem was the key is case-sensitive. If you entered  the WEP uppercase, you should also try lowercase.
You may want to read the advice :
[http://ubuntuforums.org/showthread.php?t=172810&page=2](http://ubuntuforums.org/showthread.php?t=172810&page=2)
Someone solved by deleting the connection and letting another one be automatically created with default values.
[http://ubuntuforums.org/showthread.php?t=1458905](http://ubuntuforums.org/showthread.php?t=1458905)

---

### Post by robert shearer on 2010-06-11
If you can't get your wireless working then you may be interested in this as a means to download, update and install the codecs (and anything else you may need)

[http://keryxproject.org/](http://keryxproject.org/)

---

