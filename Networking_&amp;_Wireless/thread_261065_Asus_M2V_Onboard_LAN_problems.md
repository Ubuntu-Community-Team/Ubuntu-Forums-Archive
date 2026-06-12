---
title: "Asus M2V Onboard LAN problems"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by offramp13 on 2006-09-19
I have an ASUS M2V Motherboard, it has gigabit lan on it. When i first installed ubuntu it didnt even recognize the device so i had to install it using the drivers from the site. A week or two ago i purchased a gigabit router and was excited to be able to use the full potential of it. Just a few days ago my internet started being really slow, and then my file transfers between computers was going 50 kb/s, and i knew something was wrong. Now this afternoon i was browsing and it just stopped working in whole, so i looked at the networking panel and saw that the connection was gone! So i reinstalled all of the drivers, and it was working again, but was going super slowly. I can get speeds that are like 50 times faster with a 100mb card i have. So my question is, how can i fix this? or must i wait for Edgy and hope they have an integrated driver that will work?

---

### Post by tbonius on 2006-09-19
Im not too familiar with the card itself.. but you might want to check the kernel repositiories for that specific driver.  What module does it use?  I would be curious myself before I buy a new motherboard.  Also.. I have noticed a lot of consumer switches out there do no support jumbo frames for gig-E so that can be an issue as well.  Check the driver to see if you can disable jumbo framing.  Also.. what switch is this?  If nothing else you can download the latest kernel source from kernel.org and compile it yourself.

T

---

### Post by offramp13 on 2006-09-19
I have kernel version 2.6.15-26, and i am using a Gigabit DGL-4100 router. I have acheived rates of up to 20 mb/s using the very same router, so i know it is not that. Thank you for your help though.

---

### Post by knichel on 2006-11-02
I just purchased a mobo with the onboard lan ASUS M2V.  Ubuntu does not recognize the lan adapter.  How did you get it to?  Im using 6.06 LTS.

---

### Post by tigershark on 2006-11-22
Doesn't anyone have the answer to this question?

I have the same problem, ubuntu doesn't detect my LAN and I haven't got any drivers for it either :(

---

### Post by pturing on 2006-11-29
There is a linux driver on the Asus site, but I couldn't download it from their site. I googled "Attansic L1 Linux Driver" and found a place to download Linux_LAN.zip, the contents of which I then burned to a cd.

On an Edgy machine I just installed, I then put in this cd, copied the contents to another directory, went into that directory and ran:
make install

And then I was in business 8) 


Hope this helps

---

### Post by pturing on 2006-11-29
oh, and I had to run:
modprobe atl1

I expected to have to restart networking, but oddly did not

---

### Post by thomas.mcmahon on 2006-12-06
I had this same problem too, my NIC wasn't showing up in network-admin.

I downloaded the drivers from the asus website at here:

[http://support.asus.com/download/download_item.aspx?product=1&model=M2V&SLanguage=en-us](http://support.asus.com/download/download_item.aspx?product=1&model=M2V&SLanguage=en-us)

Then I burnt the Lan drivers to a CD.

Then I copied them into a folder on my new edgy install.

I cd'd into the /src directory of the driver folder.

When I tried a "sudo make install" like the previous poster said, I got an error. I had to change the "makefile" to "Makefile" (upper case a). Then it installed.

After that I did a sudo modprobe atl1

After that it all works :)

Good luck, and thanks to previous posters.

---

### Post by knichel on 2006-12-06
I appreciate the post.I will give it a try as it is currently still not working.

---

### Post by dvarsam on 2006-12-06
Hello!

I used to have an ASUS P5LD2-VM with the same problem!
I hope your Asus Mobo does NOT have an onboard Graphics Card...
Because the Asus P5LD2-VM did!

I managed to fix it - it took me about a week - but in the end I decided to return it & buy instead an ASUS P5LD2 (without onboard Graphics Card).
Of course it was more expensive, but in the end "easiness" is of more importance!
Its always better when everything gets detected during the OS install!

Anyway, this might be of help to you:

[http://ubuntuforums.org/showthread.php?t=154532&page=8](http://ubuntuforums.org/showthread.php?t=154532&page=8)

Read it all, as it should help you!

And all this, thanks to user "Pragmatist"!

Good Luck!

---

