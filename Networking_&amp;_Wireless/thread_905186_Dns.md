---
title: "Dns"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Gandalf6596 on 2008-08-30
I am brand new to Ubuntu and to this forum so if this is a dumb question or already answered, my apologies.

Under **Network Settings**, I am setup as:
[B]Wired connection 
Address: dhcp[/B]

When I start up my computer, the DNS seems to be a default IP address.
With this IP address I can not reach the websites I want.
I added the ISP IP addresses I am connected to.

If I manually select these IP addresses, I come up on line.
I would like these IP addresses to be the default addresses so I do not have to manually select them each time I startup my computer.

Is this possible and if so how do I do it?
Please remember, I need baby step answers.

Thanks...

---

### Post by Tom--d on 2008-08-30
Baby steps made he laugh :P Thanks :D

Right,
I guess your router gives you its IP address and then the router dirverts that to your ISP DNS severs.
But for static and make it perminat.
Do this in terminal:
```
gksu gedit /etc/resolv.conf
``` and were it says namesevers:
Change it to:
```
nameserver xxx.xxxx.xxx.xx
nameserver xxx.xxxx.xxx.xx
```
x being your ISP DNS severs.

---

### Post by Gandalf6596 on 2008-08-30
Thanks **Tom--d** for the timely reply and the baby steps. :)

I followed your instructions and save the changes.  However, the changes didn't take.
The original "default" DNS Server IP address is still in place when I startup my computer.

Did I miss something?

---

### Post by froebi on 2008-08-30
Hi,

recently I had problems with resolv.conf, too -- and still have. It might be that other services take control over resolv.conf. Two I can think of are pppd and NetworkManager. Also dhcp-client is changing resolv.conf, I think. If you have NetworkManager (package network-manager) installed, this might be the source of your problem (In my case it was).

I know this is not a solution, and I'm not an expert, but maybe others can make something of if. My observation is that in some circumstances you have services that are competing over resolv.conf making it difficult to diagnose what's going on.

Christian

---

### Post by Gandalf6596 on 2008-08-30
Thanks **Christian**, I understand where you're going with that idea.
I just don't know how to determine if there are any parent processors governing the **resolv.conf **nor how to kill them for purposes of modifying the file.

Appreciate any guidance offered.

---

### Post by caljohnsmith on 2008-08-30
Gandalf6596, how about just setting up a network profile in Network Manager (System > Admin > Network), and manually specifying your ISP's DNS? There is a "DNS" tab in Network Manager where you can manually enter in your DNS, and then you can click the disk icon near the top to save it as a network profile (location they call it).

---

### Post by Gandalf6596 on 2008-08-30
[FONT=Times New Roman][SIZE=3]**caljohnsmith**, thanks for the reply.  [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]Your idea is what I did to get on line to begin with.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]However, I would like to make the change perminent and not have to change the setting every time I boot up.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by caljohnsmith on 2008-08-30
OK, I thoroughly combed through my notes, and I believe you can make those DNS changes permanent by disabling IPv6. It's simple, so you have nothing to lose by trying; just see [this page]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") on ubuntu.com of how to do it. Let me know if that works.

---

### Post by bab1 on 2008-08-30
> However, I would like to make the change perminent and not have to change the setting every time I boot up.

I believe that the DHCP server is overwriting the resolv.conf file.  Check the settings for DHCP.  If this can't be done I would manually set up static IP addressing and eliminate the DHCP sever altogether.

---

### Post by Gandalf6596 on 2008-08-30
> **caljohnsmith said:**
> OK, I thoroughly combed through my notes, and I believe you can make those DNS changes permanent by disabling IPv6. It's simple, so you have nothing to lose by trying; just see [this page]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") on ubuntu.com of how to do it. Let me know if that works.
 
**caljohnsmith**, I disabled the IPv6, but it didn't solve the problem.
 
**bab1**, how would I do what you suggested?
Remember, I'm no expert.
I'm like a long tailed cat in a room full of square dancers.

---

### Post by Tom--d on 2008-08-30
Found it!
Do these below:

```
gksu gedit /etc/dhcp3/dhclient.conf
```

Find the lines

```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
```

And change them to

```
prepend domain-name-servers 1.2.3.4, 1.2.3.5;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;
```

Replace 1.2.3.4 and 1.2.3.5 with the addresses of your DNS servers.

---

### Post by Gandalf6596 on 2008-08-30
**Tom--d**, you win the prize. Thanks to all the gurus for the assist.
I've been a Tech Staffer at PCHELPFORUM.COM for about a year (Gandalf) and I can tell you that you guys sure hold up your end.
 
Thanks for sticking with it. Now on to the next problem ...drivers. But that's another story.
 
Post Script:  This fix appended my DNS Server IP addresses in front of the one that was already there.  But, it works.

---

### Post by Tom--d on 2008-08-30
> **Gandalf6596 said:**
> **Tom--d**, you win the prize. Thanks to all the gurus for the assist.
I've been a Tech Staffer at PCHELPFORUM.COM for about a year (Gandalf) and I can tell you that you guys sure hold up your end.
 
Thanks for sticking with it. Now on to the next problem ...drivers. But that's another story.
 
Post Script:  This fix appended my DNS Server IP addresses in front of the one that was already there.  But, it works.


nice :)
Glad I could help.

so.. Drivers problem? Explain

---

### Post by Gandalf6596 on 2008-08-30
> **Tom--d said:**
> so.. Drivers problem? Explain
OK.  I listen to CDs on my computer.  I don't have a sound card or anything like that and I don't try to make the windows shake with the music, but in order to hear the music:
1. the Ubuntu speaker slide is at max
2. the Rhythmbox 0.11.5 speaker slide is at max
3. the speaker's volume control is at max

and I am just hearing the music.

With all these controls maxed out, my ears should be ringing.
When I put the same CD in my laptop (with Vista), the volume controls are set at about 50% or less.

I can't seem to find a Device Manager like Vista has.  The System > Administration > Hardware Drivers does not indicate anything to help me.

Also, my GeForce 8400GS video card driver was downloaded through the System > Administration > Hardware Drivers and has been recognized as restricted.  By restricted, does that mean I can't get the full use out of the card?  The **Monitor Resolution Settings** does not reflect the abilities of my video card.

Do you have any answers?

Thanks...

---

### Post by froebi on 2008-08-30
Hi Gandalf6596,

glad to hear you could fix your network problem. But I'm wondering if this really is the solution to the problem. In your initial post you said that your ethernet device is configured via DHCP. Doesn't that imply that the DNS servers you should use are sent to you by the DHCP server? In that case, the fix you applied is merely a workaround, I guess. Usually you wouldn't even know the IP-addresses of the nameservers to use.

Or am I missing something here?

cheers,
  Christian

---

### Post by caljohnsmith on 2008-08-30
> **Gandalf6596 said:**
> OK.  I listen to CDs on my computer.  I don't have a sound card or anything like that and I don't try to make the windows shake with the music, but in order to hear the music:
1. the Ubuntu speaker slide is at max
2. the Rhythmbox 0.11.5 speaker slide is at max
3. the speaker's volume control is at max

If you right-click the speaker icon, you can open up the mixer window that has all the volume controls (I'm in Kubuntu right now, so this is from memory). Or you can also get the mixer window by going to System > Prefs > Sound I think.

But the bottom line is that the final speaker loudness will depend on both the master volume and PCM volume. In general it is best to set PCM volume for 74% or less, because any more than that implies digital amplification, which can lead to distortion in certain circumstances. So try setting PCM for about 74%, adjust master volume, and if it still isn't loud enough, try running up the PCM volume. Let me know if that helps your sound issue or not.

---

### Post by cariboo on 2008-08-30
> **Gandalf6596 said:**
> OK.  I listen to CDs on my computer.  I don't have a sound card or anything like that and I don't try to make the windows shake with the music, but in order to hear the music:
1. the Ubuntu speaker slide is at max
2. the Rhythmbox 0.11.5 speaker slide is at max
3. the speaker's volume control is at max

and I am just hearing the music.

With all these controls maxed out, my ears should be ringing.
When I put the same CD in my laptop (with Vista), the volume controls are set at about 50% or less.

I can't seem to find a Device Manager like Vista has.  The System > Administration > Hardware Drivers does not indicate anything to help me.

Also, my GeForce 8400GS video card driver was downloaded through the System > Administration > Hardware Drivers and has been recognized as restricted.  By restricted, does that mean I can't get the full use out of the card?  The **Monitor Resolution Settings** does not reflect the abilities of my video card.

Do you have any answers?

Thanks...

To solve your audio problem first, double click the speaker icon on the right side of the top panel, that will bring up the volume control window turn up PCM until it is loud enough for you.

Restricted drivers doesn't mean they disable some functions of you graphics card, it means that the drivers are non-free as in they are proprietory code not open for regular users to modify as they see fit. Some day if you are bored, turn off usplash and watch the messages go by, if you are quick enough you will see a message that the kernel is tainted because of the non-free or restricted driver.

---

### Post by Tom--d on 2008-08-30
> **Gandalf6596 said:**
> OK.  I listen to CDs on my computer.  I don't have a sound card or anything like that and I don't try to make the windows shake with the music, but in order to hear the music:
1. the Ubuntu speaker slide is at max
2. the Rhythmbox 0.11.5 speaker slide is at max
3. the speaker's volume control is at max

and I am just hearing the music.

With all these controls maxed out, my ears should be ringing.
When I put the same CD in my laptop (with Vista), the volume controls are set at about 50% or less.

I can't seem to find a Device Manager like Vista has.  The System > Administration > Hardware Drivers does not indicate anything to help me.

Also, my GeForce 8400GS video card driver was downloaded through the System > Administration > Hardware Drivers and has been recognized as restricted.  By restricted, does that mean I can't get the full use out of the card?  The **Monitor Resolution Settings** does not reflect the abilities of my video card.

Do you have any answers?

Thanks...

Of course enable the drivers for your graphics card!
What the restricted means is that the drivers are closed soruce. Not open source. 
Thats all!
Enable them from Hardware drivers! :D:D

---

### Post by Gandalf6596 on 2008-08-31
[FONT=Times New Roman][SIZE=3]Hi Guys, ):P[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]As for the Audio, no joy. ](*,)[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]The **System > Preferences > Sound** devices **Test **is actually louder than the CD. [/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]I found the** Master** and **PCM** controls on the **Volume Control: HDA Intel (Alsa mixer)**. Unfortunately, at 75% I would have to use the speakers like headsets in order to hear any music. I know I never like music that "came through the walls", but this is a little to soft even for me. The DVD drive is an new one. It connects to a SATA port just like the HDD. Would that explain the volume problem?  Is it to new for the Ubuntu driver?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 


[FONT=Times New Roman][SIZE=3]As for the video card, I was thinking :confused:. The monitor I'm using (old) connects to the DB15 port on the video card. Would that have an affect on the video card's performance[/SIZE][/FONT][FONT=Times New Roman][SIZE=3]? I can't afford a new monitor right now.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Again, thanks guys for the input.[/SIZE][/FONT]

---

