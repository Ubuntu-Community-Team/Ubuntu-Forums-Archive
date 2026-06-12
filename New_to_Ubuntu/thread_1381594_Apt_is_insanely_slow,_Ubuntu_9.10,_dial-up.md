---
title: "Apt is insanely slow, Ubuntu 9.10, dial-up"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by souta95 on 2010-01-14
A couple weeks ago I started having a problem where downloads from the repositories were unusually slow, even for dial-up.

I have tried a few different mirrors with the same results.  Download speeds will start out at around 3-4KBps then suddenly drop off to about 200Bps, yes, Bps as in Bytes per second, then pretty much stall completely with an occasional "spike" to around 70-80 Bps every couple minuets.

Web browsing with Firefox (3.5.6) and Instant messaging with Pidgin appear unaffected.

My modem is an external v.92 RS-232 modem from TrendNet.  I am using Gnome-PPP to connect to the Internet.  Not sure of actual connection speeds but in Windows on a Conexant ACF-based v.92 USB modem they average about 28.8K.

Using Ubuntu 9.10 32-bit.

There are two user accounts on the computer, both are affected.  I use Firestarter Firewall and the problem exists weather it is running or not.

This happens when trying to download a package and when updating the package lists.  It affects Synaptic, and apt-get and aptitude on the command line.

Shortly afterwards I started having Issues with Firefox not remembering logins for Echofon and Gmail Notifier addons as well as "remember me" buttons on websites.  I doubt this is related, though as the other user account is unaffected by this, at least the web page logins, Echofon and Gmail Notifier aren't installed for that profile.

Please help, this is driving me nuts!

---

### Post by Bartender on 2010-01-15
Without being there to look over your shoulder, all I can think of is generic troubleshooting.

IN-HOUSE WIRING: Can you go to the phone co's network interface box (NIB) on the side of the house and connect a phone line right there?  If you have an ancient NIB this will be a pain, but most NIB's installed in the last ten-twenty years have an owner-accessible hatch that opens to a test plug.  If you get a good connection at the NIB, you'll have to inspect your in-house wiring for corrosion or rodent damage.

MODEM: Can you swap the TrendNet modem for a different external?  If you're like me, you've collected several external modems.  

SWAP PC's:  Can you get a couple of friends to bring their Windows or Linux PC's over and see what kind of connect speeds they get?

TALK TO YOUR NEIGHBORS:  Is everyone on the street suddenly seeing horrible connect speeds?

TRY A DIFFERENT OS:  Puppy Linux on a thumbdrive might be the easiest way to do this.

GO SOMEWHERE ELSE: Can you toss your whole rig into the car and set it up at someone's house in town, where they probably have a better connection?

You're gonna have to narrow it down.  Is the problem right inside your PC?  The modem?  The in-house wiring?  Or is it somewhere between your house and the phone company's switching facility?

---

### Post by d3v1150m471c on 2010-01-15
If it's only things you're downloading from the repositories then it very well may not be you having the issue, especially if this just started happening out of the blue. The repo's servers may be busy. Try waiting till later at night when less people are online and see if you come across an increase in DL speed. Check out something called "axel". You can also configure it to use the flashgot-addon in your firefox or swiftfox browser.

---

### Post by souta95 on 2010-01-15
I first noticed the problem when I had let updates go overnight.  There were about 30MB of updates, over a period of about 8 hours it only downloaded about 6MB.  In the past I had let about 75MB download overnight and it finished in about 5 hours.

The servers I tried were the generic US one, the one at wmich.edu (Western Michigan University, I believe), and the worldwide server - all with the same results, no matter what time of day.

I have an old Compaq Armada that is running Xubuntu 9.04 and Windows 2000 that has no problems, but I use the ACF modem on it.  I will try the TrendNet modem on that one when I get a chance.  My only other Linux machine is my netbook so I can't try the TrendNet on it.

There is an issue with either Ubuntu 9.10 or my ACF modem because it is only detected intermittently, and never responds to the connect commands ("Modem not responding"), however has no issues with 9.04 on my Armada.

The only other hardware modems I have are a 14.4k US Robotics Sportster and a Viva 9600 modem made in the 1980s.

I'll try to take it to a friend's house to see what happens, but it may be a while before I have time to do that.

I'm not familiar with axel, I'll look into it, though.

Thanks for the suggestions, I'll post back with my results when I can.

---

### Post by JimInLakeland on 2010-01-15
One thing to keep in mind - most telephone companies are only required to guarantee 9600bps on their lines. Perhaps the problem is with the phone company.

---

### Post by souta95 on 2010-01-16
I think its an issue with the computer, I'm using the TrendNet modem on my Compaq Armada and was able to update the package list just fine.  I beleive Phone companies around here require at least 14.4K.  Are the servers for 9.10 and 9.04 different? perhaps my ISP is filtering connections, its dialinfree.net

---

### Post by Bartender on 2010-01-16
> **souta95 said:**
> My only other Linux machine is my netbook so I can't try the TrendNet on it.

Why do you say that?  Because it doesn't have a serial port?  Check out the Sabrent [SBT-USC1M]("http://www.google.com/products/catalog?hl=en&resnum=0&q=Sabrent+USC1M&um=1&ie=UTF-8&cid=12906633143473328358&ei=p8VRS4XFGYXOlQeEr5TGDg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers").  Serial-to-USB adapter cable.  I have two of them.  They're supported in the kernel, so they "just work".  Well, you'll have to go back into wvdial or Gnome-ppp or whatever dialer you use and re-acquire the modem.  It should show up as ttyACM0 instead of ttyS0 or S1.
I agree with JiminLakeland.  Was trying to help some friends with abysmal dial-up speed.  Called Qwest.  The rep explained that they only "have" to supply voice, which is right around 9600.  I guess we're supposed to be all grateful and s**t if they give us anything better than that.

---

### Post by souta95 on 2010-01-16
> **Bartender said:**
> Why do you say that?  Because it doesn't have a serial port?  Check out the Sabrent [SBT-USC1M]("http://www.google.com/products/catalog?hl=en&resnum=0&q=Sabrent+USC1M&um=1&ie=UTF-8&cid=12906633143473328358&ei=p8VRS4XFGYXOlQeEr5TGDg&sa=X&oi=product_catalog_result&ct=result&resnum=3&ved=0CBEQ8wIwAg#ps-sellers").  Serial-to-USB adapter cable.  I have two of them.  They're supported in the kernel, so they "just work".  Well, you'll have to go back into wvdial or Gnome-ppp or whatever dialer you use and re-acquire the modem.  It should show up as ttyACM0 instead of ttyS0 or S1.
I agree with JiminLakeland.  Was trying to help some friends with abysmal dial-up speed.  Called Qwest.  The rep explained that they only "have" to supply voice, which is right around 9600.  I guess we're supposed to be all grateful and s**t if they give us anything better than that.

I seen them, but I don't have the money to get one right now...  I'm at a friend's house right now running updates on it, getting about 150K/sec on a 1.5Mbps DSL connection in Synaptic.

The phone liens to my house have not been replaced or upgraded since phone service was introduced to the area, probably in the 1960's, maybe the 1950's.  Its a very rural area and the phone company (Verizon) doesn't even offer DSL in the city to my knowledge.

---

### Post by Bartender on 2010-01-18
Thank goodness for friends with broadband!

Our phone lines are buried, also probly from the 60's or thereabouts.  The junction boxes along the road get water-logged in the winter.  We can see the connection speed droop for a few days after a bad rainstorm.  Sheez.

---

