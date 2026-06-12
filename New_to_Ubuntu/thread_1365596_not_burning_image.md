---
title: "not burning image"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by dubboi on 2009-12-27
hi,
can anyone tell me (as im a complete novice)how the heck im supposed to "burn image"?

i have downloaded the the ubuntu file

ita opened with roxio  but when i click on the "burn image" tab it just says -

"image file selected is not a valid file"

iv downloaded twice to see if it didnt do it properly the first time but it says exactly the same

so now im stumped

help me pleaaaassse !!!  lol

---

### Post by Teber on 2009-12-27
when opening brasero and selecting burn image you will be prompted to select a disk image to write to cd or dvd. the file you select should have the extension .iso.

hope this helps.

---

### Post by taurus on 2009-12-27
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29|%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29|%28iso%29)

---

### Post by kansasnoob on 2009-12-27
Try Infra Recorder as described here:

[https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

Unless you have Win 7 which has it's own iso image burner.

---

### Post by dubboi on 2009-12-28
ok

i managed to burn the image to cd and it rebooted  onto my pc
was working for maybe 5mins 
 

now its just crashed EVERYTHING 
i can get a single thing to work at all
i just have a dark grey screen

no keys work ,i cant eject the cd
a big fat zero!!!!!!!!!!!

iv had to unplug it at the wall to turn it off
when i plugged it back in again i had to quickly eject the cd(as i turned it on once and it just went straight to grey screen and froze the whole thing again)

then all the windows went all to cok the display screen was all about 100mm to the left and i had to do a system restore for it all to work again

i was recomended this ubuntu by a friend and now im wondering if it gonna do more damage than good!!!!!

any answers?

id still like to use it but i dont wanna have to keep unplugging it  or have it damage my pc

---

### Post by TBABill on 2009-12-28
After you created the CD, did you then try to run it "live" or did you go right for an install? I'd recommend verifying the .iso is not corrupt before doing anything else because it sounds like it is in some way corrupted. Once you get a copy burned to a CD as an image, then I would recommend running it in "live" mode first just to see if it will come up and operate, and to what degree (if all drivers work or if you will need to tweak).
 
One of the recommendations when you make a live CD is to burn at the slowest speed your burner can operate at. For me it's 2.4x speed. I am not sure why, but I suspect it is to minimize the chance for disk writing errors. If you didn't manually set your burner slower you may have some success burning a CD after that if you are able to verify the .iso is ok.

---

### Post by Portable_Jim on 2010-01-03
The first step is to verify that the CD image (.iso file) is correct. From Windows:

[LIST=1]
[*]Download WinMD5Sum from [here]("http://www.nullriver.com/products/winmd5sum") ([direct link here]("http://www.nullriver.com/downloads/Install-winMd5Sum.exe")) and install it.
[*]Choose the .iso file that you downloaded (might be called ubuntu-9.04-desktop-i386.iso)
[*]Copy the text in the "MD5 Sum" box (you can select the text).
[*]Try to find the text on [this]("https://help.ubuntu.com/community/UbuntuHashes") page. It has to be exact.
[*]If you can find the text, and it is on the same line as the file name that you have, then the image is correct.
[/LIST]
If the file is correct, you can burn it to disc.

As you have already burnt a CD, I assume you know the method of how to do it (Open up InfraRecorder => "Write Image" => Select image to write). Just before you burn, change the "Write speed" to the lowest speed (2x is low enough, however it may not be available).

Note: attached images help with descriptions.

---

