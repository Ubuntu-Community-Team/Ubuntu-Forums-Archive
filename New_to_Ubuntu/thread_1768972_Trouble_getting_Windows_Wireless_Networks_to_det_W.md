---
title: "Trouble getting Windows Wireless Networks to det WNA 3100"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Wiredless on 2011-05-27
I'm a newbie to Ubuntu who is really drowning here. I had Ubuntu installed on my Acer One and loved it until I dropped it the other day. Tight for cash, I went cheap and got a Gateway LT27 with Windows 7 start up installed. Hated it. Lovely mouse that works great with Ubuntu, didn't work at all. So, I installed Jaunty Jackalope 9.04. And looking at the posts it seems even more complex than usual to get Ubuntu to detect the pre-installed wireless card, Atheros 9285. I got the .inf file for it and got the windows wireless detector installed, but it wouldn't take the .inf file. 
 
So, I bought a plug-in Netgear Wi-fi card WNAN3100. And the windows wireless detector installed the .inf file, but won't do anything with the .sys file. 
 
Drowning...found an Ubuntu post that suggested upgrading to ndiswrapper-1.56.tar.gz. 
 
So, first question: I saved the tar.gz to the Desktop and cd'd there in terminal and followed the directions, but it won't ./configure the file. How do I configure this file? Step by step if possible. 
 
Second question: AFter that the poster her in Ubuntu said, 
 
the wrapper for IoUnregisterPlugPlayNotification needs to be added to ntoskernal_io.c at the bottom of the file-
 
wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
(void *tag) /* Don't ever use this pointer */
{
TRACE2("%p", tag);
TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}
 
I'd ask him, but it wasn't a basic forum and i'm pretty basic level. Am I going in the wrong direction here. I hate to say Uncle and try to reinstall 7.0 starter. 
 
any help greatly appreciated!
Wiredless

---

### Post by BrandonC19 on 2011-05-27
Welcome to the Forums.
You say you've installed 9.04 "Juanty Jackalope". That release is 3 years old. Is there a reason you haven't
tried a newer release such as 10.04 LTS "Lucid Lynx", 10.10 "Maverick Meerkat" or 11.04 "Natty Narwhal?"
With one of these newer releases your wireless might work OOTB (Out Of The Box).

---

### Post by Wiredless on 2011-05-27
You think it would help for me to upload to a newer version of ubuntu?   karmic or something even more recent?

---

### Post by Wiredless on 2011-05-27
sorry...i did that in high school too...somebody give me the answer, and i'd say, "oh, maybe that's the answer," and they'd say, yes i just said that...
 
the reason?  i had the disk lying around...i'll try the newer one and maybe it will just work...  or work a lot more easily and have more recent programs on the usb.

---

### Post by BrandonC19 on 2011-05-27
Haha it's alright I do i too. :p
Yea try a newer release such as 10.10. 11.04 is great but a lot of people are not too happy with the new Unity interface, so you might have a shock with that one.

---

### Post by wep940 on 2011-05-27
And........if it still doesn't install it by default, don't jump to ndiswrapper yet.  Instead let's take more time with it and see if we can find a native solution.  I have nothing against ndiswrapper, but there are a lot of drivers available out there now.

So, if it still isn't installed, please post the output of each of the below back here:

lsusb  (sometimes the internal wireless on a laptop is actually connected to internal USB)

lspci

lshw -C network

iwconfig


Also, something to keep in mind -> ndiswrapper works *ONLY* with Windows XP device drivers, and the architecture must match your Ubuntu architecture - 32-bit or 64-bit.

---

### Post by Wiredless on 2011-05-27
one more question...will natty 11.04 desktop download offer an option to work on a netbook.  having a hard time finding a link to just a netbook version, but there's something called 'unity,' being mentioned.

---

### Post by BrandonC19 on 2011-05-27
They phased out Ubuntu Netbook Edition with the release of 11.04 as Ubuntu Netbook Edition used "Unity" as it's desktop, which is what 11.04 is doing now. So the Desktop Edition is technically the Netbook Edition.
But, if you're looking for a netbook-tailored distro, you can check out: Easy-Peasy, JoliCloud, and Aurora (formerly Eeebuntu).

---

### Post by Wiredless on 2011-05-27
Thank you!   Count that solved...Maverick Meerkat (sp), 10.10, detects the inbuilt windows adpater Atheros 9285 just fine...so, I guess it's a 20% reduction in cost and cut the losses on the open box plug-in!    Meerkat seemed to get the best reviews on this score, and it works...now, I have to figure out what a Meerkat is.    I'd rather be a Koala, but maybe once you get to know a Meerkat!
 
Count this one solved!
 
Isn't Windows 7.0 starter awful?    I hate to criticise anything that can theoretically be installed for free from the Internet, but if it messes with hardware, there's a good bait and switch argument!   I may just not have been used to this mouse, though! 
 
Well, gotta go...hope the boss doesn't catch me!   I only use the Internet for things like this every two years, but he would be mad, even though it's after hours!
 
Happy Memorial Day!

---

### Post by BrandonC19 on 2011-05-27
You are welcome. Windows Se7en is a pretty good OS, but Starter is pathetic. Happy Memorial Day!

---

