---
title: "Changing wifi adapters"
date: 2021-07-13
forum: Networking &amp; Wireless
---

### Post by Autodave on 2021-07-13
I have an HP Stream That was given to me.  It works great except for the wifi.  Sometimes I show full power and sometimes a have so little that even being only 5 feet away from the router, I lose signal and have to move closer.  Anyway, I ordered a USB wifi stick.  I am assuming that it will be easy to deactivate the internal one and then activate the USB one?

---

### Post by chili555 on 2021-07-13
Are you willing to try a few remedial steps first?

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
    
```
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

   ```
 sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS

```
Proofread carefully, save (Ctrl+o) and close (Ctrl+x) the text editor.    

Is there any improvement?

---

### Post by Autodave on 2021-07-14
OK.  Tried all of that to no avail.  What next?  The new adapter arrived today, but I am unsure of how to make it active and disable the internal one.

---

### Post by Autodave on 2021-07-14
Never mind: I figured out how to change ot.  The new cheapy Edimax works great.  Thanks for you help chili555!!!!

---

