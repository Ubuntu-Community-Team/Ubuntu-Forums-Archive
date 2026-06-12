---
title: "trouble with wireless settings in 6.10"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by hyballs on 2007-06-11
Hi folks,  I am having a problem with Network settings.  The wireless adaptor is working in the Windows section but not in the Ubuntu section.   I don't know what to put in the following -

Network name (essid)  ???

Password set to *plain (ascii)*

Network password  ???

Config set to* automatic*

I've tried a few things that didn't work!  Any help would be appreciated.

The adaptor is a TP-LINK - TL-WN650g/tl  Which is a fairly common brand in Oz

---

### Post by kevinlyfellow on 2007-06-11
I'm reluctant to answer this, but does your wireless work out of the box or have you installed the drivers?

---

### Post by hyballs on 2007-06-14
Hi Kevin,  The disk that came with the adaptor was Windows only so I had to rely on the driver already installed in Ubuntu.  I assumed that the adaptor was run off a universal code to IEEE 802.11g standards.

Are you now telling me there is a problem with the Network settings?   It's really strange cos the adaptor is locked into my named network  and shows activity to the modem!

---

### Post by kevinlyfellow on 2007-06-14
I was just wondering because many, many people post here wondering why their wireless doesn't work.  Wireless drivers are an issue with linux right now, but things are getting better all the time. 

ok, so in the terminal, you can see what networks the computer sees.

```

iwlist scan

```

Also, you may consider a program called [Network Manager]("http://www.gnome.org/projects/NetworkManager/").  This talks about its installation on dapper.  [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager)

---

