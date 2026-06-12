---
title: "IT actually helped!"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by riseringseeker on 2008-05-08
Thought I would share the result of a conversation I had with the IT help folks that oversee the wireless network I was having trouble getting connected to in a  Holiday Inn in New Jersey.

I have a [System76](http://www.system76.com) laptop that I take everywhere.  I have never had a problem connecting to a wireless signal anywhere in the world (China, Europe, Middle East, South America, you name it), but I have had trouble with the couple of Holiday Inns in the US I have had to stay at.  

Last time I could not connect I was close enough to another hotel next door I simply used their wireless signal rather than call IT and have them get confused when I didn't have a start menu to click on.

This week however, there was nothing nearby that put out a signal, so I steeled myself for the usual "We don't support Linux" response and dialed the toll free number the front desk gave me.

I was most pleasantly surprised when instead of (more or less) politely telling me to go away, the guy actually was willing to work with me, apologizing that he was not better versed in Linux.

After a little discussion about the problem I was having, and what I had tried thus far, he said he was going to generate a static IP address for me, and even knew to tell me to go to System -> Administration -> Networking to set it up on my end!

Changed it as per his instructions, and it still did not work.  Then he had me try changing the default subnet mask to 255.255.0.0 from the default 255.255.255.255, lo and behold it worked!!!

I would like to publicly thank prontonetworks for being willing to try (and succeed!) helping a Linux user connect to their wireless system.

I do have a couple of questions that someone here may be able to answer though.  1) Could I have changed the subnet mask and still been able to use DHCP?  2) Could I been able to somehow see that the default subnet mask was wrong, and what it should have been?

---

### Post by helgman on 2008-05-08
I'll try to answer your questions (with somewhat qualified guesses):

1) No. The DHCP offer contains a subnet mask. You could change it after you get it from the DHCP server but as soon as the offer is updated so is the subnet mask.

2) No, or ... not without some work. If you have access to the network and can monitor then traffic then ... maybe. But not by just looking at it. There is a whole range of network "classes" with assigned subnet masks, but the thing is that these are not fixed. Default subnet mask for 10.0.0.0 is 255.0.0.0, but there nothing that stops you designing your network so that it uses something else.

Glad to here that the support personal help you.

Regards,
Helgman

---

### Post by Nem1976 on 2008-05-08
I wonder what kind of wireless/network setup they have that would cause linux not to connect to it.  I have connected to so many secured and non-secured networks it makes me wonder.  Besides that I'm glad to hear that linux is starting the support from support centers.  I know that as a System Administrator if I didn't know the operating system like a mac I would still try and help the end user if possible.

---

