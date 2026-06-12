---
title: "Problem with wifi &quot;hardware disabled&quot;"
date: 2016-03-07
forum: Networking &amp; Wireless
---

### Post by leonardo30 on 2016-03-07
Hello everyone!
I recently bought an ASUS K501UX (model K501UX-FI115T) and installed Ubuntu GNOME 15.10 on it, in dual boot with Windows 10. I managed to solve some problems that I faced after the installation, but there are a couple of issues I don't know how to face.
One of these is a problem with wifi: every time I log in, beside the wifi symbol there's written "Hardware disabled" and I can't turn it on. However, if a suspend the notebook (for example closing it) and then re-log in, it starts working.

I looked around the web, and found other people noticing this, but I couldn't find a solution.
I've read some people being answered that the wifi must be physically turned off for sure, but on my laptop there are no physical switches for the wifi, nor is there any BIOS setting that disables it (it works on Windows 10).

The only way I could physically turn on/off the wifi is with Fn+F2, which enables/disables airplane mode. However, while this works on Windows 10, it doesn't on Ubuntu. There is also a led for airplane mode on my notebook, and in Windows it turns on/off properly if I press Fn+F2, while in Ubuntu it doesn't. Furthermore, once I have suspended the notebook and made wifi work, if I turn on and then off airplane mode from the settings, it doesn't work again and says "Hardware disabled" and the only way to make it work again is by suspending the notebook another time.
I have also noticed (but I don't know if it can be significant) that after enabling and disabling airplane mode from the settings, under the wifi appears the bluetooth symbol (even if it always works properly).

Can anybody try to help me?

Thanks

If it can be useful:
```
$ lspci | grep -i wireless
03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
```

---

### Post by jeremy31 on 2016-03-07
Post the result of ```
lsmod | grep asus
```

Have you already tried ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d.asus_nb_wmi.conf
```

Although I don't see any other Asus K models in the rfkill quirks in the linux-next git site

---

### Post by leonardo30 on 2016-03-07
Here it is:
```
$ lsmod | grep asus
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi
video                  36864  2 i915,asus_wmi

```

I hadn't tried before what you suggested, but didn't work...

---

### Post by leonardo30 on 2016-03-07
Actually, after a more careful research, I found this page:
[http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v7](http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v7)
which is basically identical to your solution, but as suggested in the answer I tried [COLOR=#111111][FONT=Consolas]wapf=1[/FONT][/COLOR] and it actually worked (while [COLOR=#111111][FONT=Consolas]wapf=4[/FONT][/COLOR] didn't). However, I have noticed that now the airplane mode led and the actual setting are reversed: in other words, if I turn on airplane mode in the settings the led turns off, and if I turn off airplane mode the led turns on. Furthermore, even if now wifi works, the Fn+F2 shortcut still doesn't work.
Even if that is not really a big problem (but I find it a bit annoying), does anybody know how to fix this?

---

