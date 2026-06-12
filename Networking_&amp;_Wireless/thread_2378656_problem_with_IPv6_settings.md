---
title: "problem with IPv6 settings"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by Hasimir on 2017-11-25
I have followed [this guide]("https://webcheerz.com/disable-ipv6-on-ubuntu/") in order to disable my IPv6 connectivity.
It works... but after a reboot it doesn't work anymore.
[COLOR=#2A2E2E][FONT=&amp]The CAT command still returns "1".
But activating a VPN and going to [https://whatismyipaddress.com/]("https://disq.us/url?url=https%3A%2F%2Fwhatismyipaddress.com%2F%3AGjUv8qoYAFtuSiiTrkPP8MJsKY8&cuid=4328762") shows MY REAL location.[/FONT][/COLOR]
[COLOR=#2A2E2E][FONT=&amp]If I run again the "**sudo service procps reload**" command, then everything works again... until next reboot.
What can I do to fix this?[/FONT][/COLOR]

---

### Post by missmoondog on 2017-11-25
you can't simply disable ipv6 in your router, if you're using one? don't know why anyone would want that disabled anyway though?

---

### Post by Hasimir on 2017-11-25
> **missmoondog said:**
> you can't simply disable ipv6 in your router, if you're using one? don't know why anyone would want that disabled anyway though?
Simply put, the whole point of using a VPN for me is to make my computer anonymous on the web.
As long as the IPv6 protocol is active I am not anonymous, as it just takes a simple trip to a website such as whatismyipaddress.com to reveal my exact identity and position.
If you know of another way to fix this problem while keeping the IPv6 protocol active, I'm all ears :)

---

### Post by #&amp;thj^% on 2017-11-25
> **Hasimir said:**
> Simply put, the whole point of using a VPN for me is to make my computer anonymous on the web.
As long as the IPv6 protocol is active I am not anonymous, as it just takes a simple trip to a website such as whatismyipaddress.com to reveal my exact identity and position.
If you know of another way to fix this problem while keeping the IPv6 protocol active, I'm all ears :)

Hi Hasimir Give this a try first if you are using Firefox:
in the firefox URL: Enter this>>**"about:config"**: set to **"false"**>> "geo.enabled".
If that works for you then you will have to check that regularly it seems to change.

---

### Post by Hasimir on 2017-11-26
I don't use Firefox. I use Chrome.
But I think this is irrelevant.
I want my system to be anonymous on the web, like while using programs and apps such as Transmission. Not my browser, necessarily.
Is the IPv6 vulnerability only relevant to browsers?
Is a program like Transmission simply "a different matter" and is it not touched by this IPv6 leak?

---

### Post by #&amp;thj^% on 2017-11-26
> **Hasimir said:**
> I don't use Firefox. I use Chrome.
But I think this is irrelevant.
I want my system to be anonymous on the web, like while using programs and apps such as Transmission. Not my browser, necessarily.
Is the IPv6 vulnerability only relevant to browsers?
Is a program like Transmission simply "a different matter" and is it not touched by this IPv6 leak?

Would have been good to know that at the begining.
To check that transmission is not leaking your info go here:
[https://ipleak.net/](https://ipleak.net/)
Next Activate the Test from the Section: Torrent Address detection
It will give you a magnet to open with transmission, and report any findings.
BTW The majority of the VPN providers Strongly state to not use Chrome. (Your Choice)

---

### Post by Hasimir on 2017-11-26
Sorry, I didn't think that was relevant at the beginning of the thread >__<

So...
Without the **sudo service procps reload** command the IP is masked (becomes Russian, Japanese, Korean, whatever) but the torrent check reveals that I am in Germany, Hamburg. My true position.
With it the check says I am in Germany, Berlin. Not sure it's supposed to happen?
Which steps can I take to better hide my torrent activity?

---

### Post by #&amp;thj^% on 2017-11-26
No worries, but the more information you provide the more likely We or I don't miss what you want to accomplish.:)
I would open a ticket with your VPN provider,
I successfully disabled IPv6 once putting the following lines in "**/etc/sysctl.conf**":

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

After adding the lines to sysctl.conf, run:
```
 sudo sysctl -p
```
or reboot to let changes take effect. 
I would be very surprised if was related to IPv6 though.
Good Luck :)
BTW it should be clear how to re-enable  IPv6 right?

---

### Post by Hasimir on 2017-11-26
I assume removing those line and rebooting should restore the original parameters? :)

---

### Post by #&amp;thj^% on 2017-11-26
Yes! you are correct.
Or simply use this on the fly after removing the lines. (No Reboot needed)
```
 sudo sysctl -p
```
Let me know if that works, not leaking your information. (I'm very curious ;))

---

### Post by Hasimir on 2017-11-26
Now it works.
I've tested it.
I'll check again tomorrow, after an actual reboot.

I found this method earlier in my search, but read that it was not ideal as the conf file might get overwritten during a system update or upgrade, without warning.
But so fat it looks like it's the only method that actually yelds reliable results.
Thanks for this!

---

### Post by #&amp;thj^% on 2017-11-26
Good to hear! :)
It has never changed for me in about a year of usage.
I need to edit my post where I said it was enabled on my end.
Cheers

---

### Post by Hasimir on 2017-11-26
I was too curious and did a quick reboot right now.
The effect is gone.
If I run my vpn (it is the program **GvpnGate**) and go to the ipLeak.net site my IP is masked but my IPv6 is not.

If I run again the command [COLOR=#000000][FONT=&quot]sudo sysctl -p[/FONT][/COLOR] the effects resumes immediately, both my IP and IPv6 are masked.
Is there a way to make this stick between reboots?

---

### Post by #&amp;thj^% on 2017-11-26
Well the only way I know how to do this on system start-up is through Grub.
Now we all know that changing grub can have very bad effects on some systems.
I guess you could try it once without editing Grub permanently. 
By adding this:
```

GRUB_CMDLINE_LINUX="xxxxx **[COLOR="#FF0000"]ipv6.disable=1[/COLOR]**"

```
If that works on your first try make it stick by adding it to "/etc/default/grub"
**EDIT I can now confirm that this works on system startup.**

---

### Post by Hasimir on 2017-11-27
In my GRUB file I have a line:
GRUB_CMDLINE_LINUX=""

Should I add a new line?
```

GRUB_CMDLINE_LINUX="xxxxx ipv6.disable=1"

```

Or shoud I add the string "xxxxx ipv6.disable=1" within the empty string of the original line?

---

### Post by Hasimir on 2017-11-27
No joy :(
After reboot my IPv6 is clear as the sun.
Just to be sure, my GRUB file now looks like this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="xxxxx ipv6.disable=1"

```

Again, if I run the **sudo service procps reload** command everything becomes airtight again.
Is there a way I can turn this into a script that will launch at every boot?

---

### Post by #&amp;thj^% on 2017-11-27
> **Hasimir said:**
> No joy :(
Again, if I run the **sudo service procps reload** command everything becomes airtight again.
Is there a way I can turn this into a script that will launch at every boot?
Not that I know of.
But you should try it this way. Sorry I assumed you would know what I meant.:(
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"

```
Don't forget to let grub know about the change with:
```
sudo update-grub
```

---

### Post by Hasimir on 2017-11-28
This way it works! Thanks a lot! :D

---

### Post by #&amp;thj^% on 2017-11-28
Great! ;) Your very welcome.

---

