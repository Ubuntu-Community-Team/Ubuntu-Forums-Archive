---
title: "Wfi only works sometimes! Ubuntu 14.04 Asus U56"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by ernestj on 2014-07-24
Help!
My wifi has been intermittent since 11.10. One of the incredible users of this forum has helped me in the past with special code that I put into terminal. 

Now with 14.04, I have not needed the code, but out of nowhere, I loose wifi for no apparent reason. The only way to get it back is to unplug laptop and remove the battery. 

If I try to add a specific driver, it does not recognize any drivers. 

I love Ubuntu and can not switch back to Windows. (Might go to the other dark-side, Apple, if I can not figure this out).

I believe the problem is specific to this laptop or wifi driver.

Thanks in advance.
Ernie

---

### Post by deadflowr on 2014-07-24
Thread Moved to **Networking and Wireless**

Hopefully someone in this area will know what to do for you.

---

### Post by ian-goodchild on 2014-07-24
Hi

Wifi is tricky on ubuntu I had to get(steal) an old dongle off Mum as my HP network card is a bitch. If you don't have a Mum with an old wifi dongle ebuyer sells cheap ones for £4ish although p&p will cost you twice that. Cheaper ones tend to work better. Do a quick search for cheap dongles,it will probably save you money. Funnily once I had the old dongle installed the network card fired up after the next update.

Cheers
Ian

---

### Post by Rob Sayer on 2014-07-25
Disregard the last post.  There's been a lot of really, really bad noob advice here lately.

No one can help you without knowing what adapter you have.  Paste this into terminal and post results here wrapped in ```
 tags:

[CODE]sudo lshw -C network
```

Also, run the wireless script.  See here:

[http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos](http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos)

There are some real wireless experts here (unlike myself) but they can't do much blind.

---

### Post by varunendra on 2014-07-25
> **ernestj said:**
> Now with 14.04, I have not needed the code, but out of nowhere, I loose wifi for no apparent reason.

Hi Ernie!

Please take a look at this thread : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)
..and confirm if your problem (and solution) is the same one.

If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
@Rob Sayer,
We all were "noobs" at some point. Ian was just trying to help. :)

---

### Post by ernestj on 2014-08-13
Thank you once again!!

I used this code and I believe this solved the problem. Thank you again!!

echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf

---

### Post by ernestj on 2014-08-13
i do not know how to change thread to "SOLVED"

---

### Post by varunendra on 2014-08-13
First - Congratulations! :)

To mark the thread as [SOLVED], use the "Thread Tools" link above the top post on the page. You can find screenshots in the "see how" link in my signature.

---

