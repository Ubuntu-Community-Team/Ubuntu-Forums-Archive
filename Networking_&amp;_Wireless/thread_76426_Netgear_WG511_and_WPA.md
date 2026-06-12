---
title: "Netgear WG511 and WPA"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by richbouchard on 2005-10-15
I really like to solve this stuff myself, but I've searched this forum and googled for hours, all to no avail.  I've found lots of info, of course, but, probably because I'm new to Linux, nothing that's got it working yet.

Has anyone got this combination (Breezy, The Netgear WG511 WiFi card, Netgear DG834G router and WPA) working?  I should say that, if I turn off all the security on my router (WPA and MAC filtering) then the card connects fine with Breezy out of the box.  But the rest of my network (couple of Windows boxes and a network printer) has been running for 2 years with WPA enabled.  I want to keep it, naturally enough.

Here's what I've done to get WPA working so far:

Followed [this thread]("http://ubuntuforums.org/showthread.php?t=26623") which details the installation of wpasupplicant, but is concerned with the ipw2200 (built in centrino?) card.

I've figured out that my card uses a different chip set.

```
lspci
```

yields the following:

"Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)"

So we're dealing with a Prism chip set.  Hence I've adjusted my startup code for wpa_supplicant.conf to:

```
sudo wpa_supplicant -B -i eth0 -c /etc/wpa_supplicant.conf -D **prism54** -w -dd
```

The card is definitely eth0 and the addition of the prism54 was by trial and error on my part.  Is there a different driver I should be calling here for the Prism GT/Prism Duette chip set?

My wpa_supplicant.conf code looks like this:

```
network={
         ssid="homenet"
         scan_ssid=1
         proto=WPA
         key_mgmt=WPA-PSK
         pairwise=TKIP
         psk="[REMOVED]"  ## <-- here I've entered my 8 digit, plain text key as entered in the router config.
}
```

I also have ap_scan=2 earlier on in the file, but I've tried with ap_scan=1 (the default?) and without pairwise=TKIP, too.  Nothing will make the card associate with the router with WPA enabled.  The little green light just sits there, flashing away to itself!  Except...

If I flip the card out of the slot and then put it back in again, the light flashes then goes steady for about 8 seconds!  Hurrah, I thought.  But no, I'm still unable to ping anything or view anything in Firefox (even the router config page at 192.168.0.1).  However, the difference now is that the 'Connection Properties' dialog shows packets received (whereas before there were only sent packets and received stayed stubbornly stuck on 0).

I sense that I'm very close at this stage.  But I just can't make the final intuitive leap to get this working.  Anybody spot an obvious mistake?

Thanks,

Rich

---

### Post by kgreiner on 2005-10-15
when ever i have to set up wpa_supplicant I usually follow this post in to forums.

[http://ubuntuforums.org/archive/index.php/t-31418.html]("http://ubuntuforums.org/archive/index.php/t-31418.html")

---

### Post by richbouchard on 2005-10-15
Thanks for the quick reply.  Unfortunately, following that thead was slightly worse!  One or two of the commands threw up problems (e.g. the chmod 600 for the .conf file caused the debug info to show an unable to access file error, had to chmod back to 777).  In any case, I followed it step by step, adjusting for my interface, eth0, and driver, Prism54, but still no joy.

Do you (or anyone else) have any other suggestions?

---

### Post by richbouchard on 2005-10-17
Well, I messed around so much that I finally broke my installation (well, that and the 30 boot forced disk check).  So I'm reinstalling and will have another go from clean.

WPA really needs to be easier than this in future releases.

---

### Post by seiser on 2006-03-14
richbouchard, the prism54 driver does not support WPA unfortuneately. you need to use a windows driver with ndiswrapper.

---

### Post by jml on 2006-03-14
Seiser is right.  There is very little support for WPA encryption natively in Linux in general, and Ubuntu in particular.  The only way I got WPA working on a laptop was by "cheating"  When I bought my new laptop, (HP nx6110 from Spidertools.com)  I bought it with Linux (Mandriva 2006) installed and it came with wireless already configured using a Windows driver and NDISWRAPPER.  I even asked tech support to try and set up Ubuntu that way on the laptop, but after a week's trying, they told me that they could not get WPA working.  I also hope that when 6.04 comes out that it will support WPA on more chip sets.  I just can't get used to an RPM base distro.

Joe

---

