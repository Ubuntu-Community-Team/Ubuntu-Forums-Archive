---
title: "stuck in grub rescue"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by 77kwill72 on 2010-07-31
Well i finally decided to try Ubuntu.  I partitioned my external hard drive and installed Ubuntu using Wubi which went fine. Reboot, reboot got to poke around the desktop for a few and then it started to update itself.  All went well until that reboot took place.  I am now stuck with error: no such device: (long string of characters) and then a "grub rescue>" prompt that is allowing me to do nothing.

After doing some research I believe I have to go back in through a live cd and make some changes.  The problem is I know nothing about the naming of devices or what the variable notations are. 

My livecd iso just finished downloading on my alternate machine which i will burn now, but i would appreciate greatly any help on each step to take to get myself back to being able to boot to windows or ubuntu, preferably with no data loss.

Thanks in advance for any assistance.

---

### Post by TwoBee on 2010-07-31
I have the same problem.
I have installed Ubuntu 10.04 using Wubi. Then I ran the update manager and restarted to finalize installation. When I restarted I got an error saying:
> no such device: 34fbe348-db5a-4541-9ded-19390668b4d0
And the grub rescue> prompt.

Could someone help with a solution?

---

### Post by oldfred on 2010-07-31
77kwill72, Welcome to the forum. TwoBee you are also welcome but please start a new thread if you want to post your results or you can just follow along, but you issue may or may not be the same.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by 77kwill72 on 2010-07-31
Hey oldfred, thanks for the offer of assistance but because it was so long for even an acknowledgement of my post and the number of questions that were answered meantime, I got discouraged and rebuilt my mbr with windows and uninstalled ubuntu all together.  I was quite surprised actually as previous experiences on boards like this, especially for an open source project (Opera, Chromanium, etc.), usually yielded many quick responses with help and guidance.

The experience will not keep me from reinstalling ubuntu again at some point, but lesson learned I will do some reading before I jump in blindly.

Thanks again.

---

### Post by bcbc on 2010-07-31
> **77kwill72 said:**
> Hey oldfred, thanks for the offer of assistance but because it was so long for even an acknowledgement of my post and the number of questions that were answered meantime, I got discouraged and rebuilt my mbr with windows and uninstalled ubuntu all together.  I was quite surprised actually as previous experiences on boards like this, especially for an open source project (Opera, Chromanium, etc.), usually yielded many quick responses with help and guidance.

The experience will not keep me from reinstalling ubuntu again at some point, but lesson learned I will do some reading before I jump in blindly.

Thanks again.

This is a very recent problem resulting from the latest grub update that is installing (or leading wubi users to install) grub in the harddrive MBR. The fix is simple - to reinstall the windows bootloader. However, the problem is - visually - very bad, especially for a new user to ubuntu. Devs haven't responded to my bug report. [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

I don't have my regular test computer so haven't figured out all the details e.g. if the wubi install is not on the same partition with windows. At any rate, it is brand new to the forums as well - as you are wondering why it took so long to get a response.

---

