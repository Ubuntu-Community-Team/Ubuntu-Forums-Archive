---
title: "S - L - O - W wifi"
date: 2016-05-28
forum: Networking &amp; Wireless
---

### Post by cobras on 2016-05-28
[COLOR=#000000]Greetings Good People,[/COLOR]

[COLOR=#000000]I recently acquired a laptop ([/COLOR][COLOR=#000000][FONT=arial]Toshiba Satellite C55-A5286, 8GB, Intel(R) Core(TM) i3-3120M CPU 2,5GHz, 700GB HD) running Windows 8, and installed Ubuntu 16.04 along side it.

My problem is that the wifi is so slow that pages time out.  I'm posting this thanks to Windows, which does not have the problem.  A much older and slower machine running Ubuntu 12.04 also does much better despite a much lower bit rate.

Ubuntu should be completely updated after

sudo apt-get update
sudo apt-get dist-upgrade

Haven't been able to download and run the wireless info script with Ubuntu.

Please share your knowledge.[/FONT][/COLOR][COLOR=#000000][FONT=arial]
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2016-05-28
Click on the wireless script in my signature and follow the directions for running it without an internet connection.
Thanks

---

### Post by cobras on 2016-05-29
Thanks for the reply.  I think I've managed to do as you asked.

The following might be helpful to other people.

The link from the signature sends you to another thread, which sends you to another thread with more links.  It can be confusing to us newbies, especially if you're having to switch back and forth from OS to OS.

At one point a path is given ([I][COLOR=#800000]**Files > Preferences > Behavior tab > select "Ask each time"** option under "Executable Text Files" section.) that allows you to execute the script.  Instead of Files try the Edit tab.

Another thing is that I could not get the script to run until I changed the name of the script file.  You see, the name of the script is the same as the resulting file otherwise.[/COLOR][/I]

---

### Post by jeremy31 on 2016-05-29
If you can change router settings, place it on channel 9 and change encryption to WPA2-PSK, WPA2-AES, or WPA2 only without TKIP enabled

---

### Post by wildmanne39 on 2016-05-29
Also change your setting in network manager to match the screenshots that usually helps with speed and connection issues.
Thanks

---

### Post by cobras on 2016-05-30
I have a couple of questions.

First, does this mean I'll have to change the settings on every router I encounter?  Second, is there a tutorial on how to go about this you can refer me to?

Thanks.

I think I figured some of it out.

I was able to set IPv4 and IPv6 as suggested, but the only options I have in my Network Settings for WiFi Security are the following:

None, WEP 4/128-bit Key (Hex or ASCII), WEP 128-bit Passphrase, LEAP, Dynamic WEP (802.1v), WPA & WPA2 Personal, WPA & WPA2 Enterprise.

Where is the channel changed?

OK.  Thank you any way.

---

### Post by jeremy31 on 2016-06-02
Let's set the correct country code
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

We can also try using software encryption on the module with
```
echo "options rtl8188ee swenc=Y" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```

reboot

---

### Post by cobras on 2016-06-17
Hey Jeremy, I didn't have to opportunity to try your last suggestions.  Thank you to everyone for your efforts to help.  I never did get the issue resolved and ended up uninstalling Ubuntu (that was worth another thread).

---

