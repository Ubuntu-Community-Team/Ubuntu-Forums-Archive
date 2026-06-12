---
title: "Critical three-year-old Eduroam bug unresolved?"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by samthurston on 2014-08-08
I downloaded 14.04 and installed it on my school laptop.  

What a huge mistake.

I've been using linux for almost 20 years now (started with slackware on 27 floppy disks in 1995).  I know my way around the command line, networking subsystems, wireless configuration, hand-tuning xorg.conf,  kernel building, etc. I have been trying every version of ubuntu for *three years* - since 11.04 - to get it to connect to my campus student WPA2 Enterprise network, also known as eduroam.

If you're not familiar, eduroam is a little service used at 5500 educational institutions worldwide, that allow students and faculty at any university to use the wifi at any other university using an SSO.  

In three years of trying multiple guides, instructions from my Computing Support Group, installing certificates, trying esoteric wpa_supplicant configurations... the absolute best result I have ever been able to achieve, on 12.04, was infrequent connection.  Currently, the status with the approved method of configuring 14.04 for eduroam is, *it works for a minute or two, tops.*

I have spent dozens of hours trying to get this working with the** best case** being** unacceptable** for daily use. I understand that some universities use different inner authentication methods which make their eduroam setups easier.  

I would be filing this as a bug, except it's been filed over and over and over, escalated the gnome team which ultimately grades it "wontfix" and it dies. There are at least two separate bugs at play, one of which is the network-manager GUI incorrectly managing its own network profiles. - WHAT?

This is the kind of worse-than-a-papercut bug that Canonical really needs to get resources behind.  Universities are where Apple and Microsoft preen their lifetime users.  I can't even ask anyone with a straight face to support an OS that can't stay connected to one of the single largest enterprise wifi installations on planet earth.  It's shameful, it gives the cupertino/redmond crowd something humiliating to crow about, and I'm at my wits end.

---

### Post by mörgæs on 2014-08-08
If you want to discuss the bug and corresponding reports please link to them.

---

