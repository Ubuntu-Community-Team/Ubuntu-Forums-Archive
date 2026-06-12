---
title: "ubuntu refuses to install"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-09-04
im using windows 7... i partitioned the hdd into two parts. i loaded ubuntu through a flash drive.. tried to install on the partition.. but it says there is something about a root problem.. i cant figure a way to install ubuntu on the partition and i dont want to wipe windows as i love to game

---

### Post by jeight on 2010-09-04
We may need a little bit more information before we can help you. What exactly does it say about root and when does it say this. Does it give you this during install or after rebooting?

---

### Post by audiomick on 2010-09-04
> **jeight said:**
> We may need a little bit more information before we can help you. What exactly does it say about root and when does it say this. Does it give you this during install or after rebooting?
And can you boot into the "Try ubuntu without changing the computer" option?

---

### Post by Proto_Blaze on 2010-09-04
i boot from the usb and put install... and it says that it cant find the root or something...

---

### Post by krimzonstarr on 2010-09-04
I have no experience with Windows 7, have booted *buntu exlusively for +4 years now... But, how did you create the USB image (the process or application)?

---

### Post by Proto_Blaze on 2010-09-04
i made it the way the ubuntu site told me to

---

### Post by Sef on 2010-09-04
> i partitioned the hdd into two parts.

1. How did you partition the hard drive?

2. What file system are you using for Ubuntu?

---

### Post by Proto_Blaze on 2010-09-04
i used the windows partitioner... and what filesystem should it be?

---

### Post by krimzonstarr on 2010-09-05
When you boot your computer, and select the LiveUSB as the boot device, exactly what errors are you seeing (or as close as you can read/recall)? The type of filesystem you created should not matter, the ubuntu installer will prompt you to repartion as needed.

What was the source of your Ubuntu installation .iso? I have had many problems in the past with corrupted .iso downloads. Make sure to check the md5sum before trying to make a LiveUSB. I have seen many instances of LiveUSB's working just fine, until I attempted to install, thanks to a small corruption in the download.

tl;dr... Need more information.

---

### Post by Proto_Blaze on 2010-09-05
basically when i boot from the usb it works ok.. i can use ubuntu through my usb... its when i try to install it is when it gives that root error

---

### Post by Sef on 2010-09-05
> and what filesystem should it be?

Either ext 3 or ext 4. What did you choose?

---

### Post by krimzonstarr on 2010-09-05
Try checking the md5sum of the iso you used to create the LiveUSB. If there were any small corruptions during the download, it could make the system un-installable. Personally, I like to use torrent downloads, since they seem MUCH more likely to download intact.

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by Proto_Blaze on 2010-09-05
i figured out the issue.. ive installed and dual booted... what setup stuff do i need now?

---

### Post by kmsalex on 2010-09-05
> **Proto_Blaze said:**
> i figured out the issue.. ive installed and dual booted... what setup stuff do i need now?

Well the first thing i do is  go to a termianl (applications>acessories>termial) and then type

```
sudo apt-get install ubuntu-restricted-extras
```That will get you flash, java, mp3 playback capability and a few other things i can't think of off hand.
(ps you won't see your password when it asks for it, just type it in and hit enter)

Then i check to see if there are any drives available for my system, to do that go to (system>administrator>hardware dirves), if there are more then one try both (do a restart in-between and see if one is faster/more responsive then the other, if they seem the same go with the open source one.

Another thing i do is grab the latest versoin of [Ubuntu tweak]("http://ubuntu-tweak.com/") this is a great little application that lets you modify, change, or just tweak hundreds of little settings (including moving the close maximize minimize buttons if the left alignment bothers you).

And for new commers a great manule google turned up can be found [here ]("http://ubuntu-manual.org/"), best one i think I've seen, covers nearly every subject i could possibly think about, and then some.

---

