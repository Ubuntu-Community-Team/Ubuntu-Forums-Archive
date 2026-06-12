---
title: "Realtek RTL8188EE: 13.10 Wireless fails only on router requiring authentication"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by devine.steve on 2013-12-20
I have recently purchased a new Toshiba laptop. It has Win8 on one side and Ubuntu 13.10 on the other, It has been working fine since I bought it 3 weeks ago. Now all of a sudden the wireless failed.
Whats odd is that It connects fine to a older router that has no password. My newer router that requires a password just keeps failing and prompting for a password. 
It's not the router - this works on the Win8 OS and on my tablet.
I tried the following commands as suggested by Varunendra in IRC
modprobe -rv rtl8188ee
modprobe -v rtl8188ee fwlps=0 

and modprobe -v rtl8188ee fwlps=N swenc=Y


But no joy.
I also ran the wireless script and posted it here [http://pastebin.ubuntu.com/6609184/](http://pastebin.ubuntu.com/6609184/)

---

### Post by varunendra on 2013-12-22
Welcome to the forums Steve !

I was hoping someone else better than me would pick up your thread and you'd get some better advice this time since I already tried my wits on the IRC.
Still hoping for others to join us, let us proceed with some tests.

Since it used to work earlier, it's an easy guess that some update might have broken the connectivity. Assuming it may be a kernel (hence driver) update, can you boot with an older kernel? Is it able to connect with the older kernel?

Just curious - is it the default driver or you installed it from another source, like "Additional Drivers" dialogue, or compiled-installed from source, etc? My 12.04.1 doesn't have this driver and I don't have 13.10 ISO yet, so I'm not sure if it is available by default or not in 13.10.

Also, I forgot the reason you told me why you can't change the encryption in the router. Could please explain again, for me as well as others here?

The current router settings are not 'Incorrect', they are just not optimal. Windows drivers are designed by the manufacturers themselves, and tablet drivers are a lot simpler (they don't need advanced functions), so they'd obviously work better than most of the Linux drivers. But where a problem arises, it is best to keep things in their optimal state to at least pin-point the problem if not solve it.

Although we can try things without that change especially if the same driver used to work with the same settings earlier, it would be better to change the encryption to pure WPA2-PSK with AES/CCMP (no WPA/WPA2 mixed mode, no TKIP), 'If you Can'. :)

Lastly, have you tried deleting the existing connection and recreating it in Network Manager yet? If not, please try that now.

I guess my next attempt may be trying the latest backported driver if tweaking only the settings doesn't work.

**PS:**
I'd be travelling most of the time for next two days, and not sure how much busy I can get after that, so may not be able to respond quickly.

---

### Post by devine.steve on 2013-12-22
Varun,
I booted into the original install USB stick and it wouldn't work either. Now I am starting to doubt that it ever worked. It's possibe that I always was connecting to the 'other' router. I control that one with MAC addresses.

 I also figured out how to get into the router config and I was able to change the configuration as you suggested and now it works. So I quess I will leave it alone.
Thanks for all your help 
Steve

---

### Post by varunendra on 2013-12-22
> **devine.steve said:**
> I was able to change the configuration as you suggested and now it works..

That's awesome !

And it's good to see that you've already started helping others and are offering good advice. I'm glad I invited a 'Helper' among us from the IRC. :)

---

