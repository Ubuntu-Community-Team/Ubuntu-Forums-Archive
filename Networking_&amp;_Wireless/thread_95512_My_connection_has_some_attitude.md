---
title: "My connection has some attitude"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by derrick1985 on 2005-11-26
My connection keeps on phasing in and out on me. For some reason, I think it' sthe DNS because when it does go out, I can still usually connect to MSN and whatnot.

Anybody have any ideas why this is happening? My connection is through a router, high speed. I dont' have this problem in XP, so I don't think it's the router (regretably)

Thanks

---

### Post by nalmeth on 2005-11-27
I am having the same problem actually...
I have my modded xbox hooked up to the same router as my computer, and the xbox has no problems with net..
My computer however, has the same "phasing in and out" issue, and this just started happening for me yesterday. I have a network monitor in my system tray that claims eth0 is active, and seems to take in 3kb every 5 seconds or so, but browser has no internet, nor does terminal.
I thought I was totally hooped, but then I opened azureus, and it seemed to wake up the internet somehow, because it started uploading torrents, and internet was going allround all of the sudden..
Then later on in the evening, azureus was inactive, and I was allround phased out again. 
I find this very suspiscious, because I have never seen this happen before, and I've been using ubuntu since hoary, and I've never heard of this happening to anyone else..
Is it possible we have a virus on our hands?
Lets wait and see what the community has to say..

---

### Post by nalmeth on 2005-11-28
ok, now i'm really in some trouble. there is no phasing "in" anymore. All my apps are blocked off from the internet, yet my network diagnostic tools are telling me I do have an active eth0 connection. I thought at first it told me this because I had a connection to my router, but perhaps not the internet. I then tried to connect to my xbox via ftp and failed.. again my xbox has internet for sure.

An important note I forgot to mention. I live in a house with 4 other people all using internet. Our previous setup was not working because not everyones computer was showing up on the MS/Samba network (but everyone still had internet access), so we rearranged the two routers. Keep in mind my internet was working still for a brief period after the switch, although thats when the phasing began. I am using DHCP of course, so no matter the source, so long as a have a line it should work right? 

My old IP was 0.106 i think, and the DNS was 0.1, but now it is 2.107, DNS 2.1
It appears DHCP adjusted..

I am so used to linux having any problem BUT a internet connection problem, so I am lost as to what to do.
I tried a static IP, but didn't help. 

I have a terrible gut feeling that I will have to reinstall, which is VERY IRRITATING considering all I have done to set it up to my needs (setting up 32-bit chroot, setting up my apps, and everything else!), so as you all understand I'm sure, I want this to be a dead last resort. 

Luckily I had downloaded DSL 2.0 before all this, so I burned it to a disk on which I am posting this message right now. Proof enough that it is solely ubuntu that is malfunctioning. 

I ran ifconfig, and eth0 was not displayed (as I thought it should be?)

DCOP showed these programs running that I am not familiar with:
kio_uiserver
kded
kwin
kaccess
katapult_9905

However I may have installed them all on a binge and don't remember (you know how it is).

Frustrated, annoyed and handcuffed, but patiently and humbly accepting any suggestion 
      :mad:         :confused:          :(                                         :KS 
as always thanks for any you all might have..

nalmeth

---

### Post by mindwarp on 2005-11-28
Have you already went through the steps in [this thread](http://www.ubuntuforums.org/showthread.php?t=87643)?

---

### Post by nalmeth on 2005-11-28
should have seen earlier..
followed the thread and everything went fine until:

[I]
ping (i put router address here)
send msg operation not permitted
over
and over again[/I]

7 packets transmitted 0 recieved 100% packet loss

this would suggest that there is a problem with my router, but i switched back to the old one that worked before and had the exact same problem. 

the thread suggests testing with another machine, and my xbox on the same router works fine.
[I]
sudo dhclient eth0
ssit0 unknown hardware address type 776
ssit0 unknown hardware address type 776[/I]

again, my ethernet card was detected fine, card drivers all in order, I have an IP address via DHCP in accordance with the DNS through router, and every command gives me thumbs up except

ping (xyz.xyz.x.y)
sudo dhclient eth0

note: ipv6 not applicable
also internet on livecd on same computer is fine. ubuntu is malfunctioning

any ideas before i give it the hook?
still open to ideas even if i do reinstall. I would like to learn how to dig myself out of this position in future!
:p

---

### Post by derrick1985 on 2005-11-28
Glad to see i'm not the only one with this problem. I wonder if our NIC's are the same?

Anyways, I reinstalled Breezy and everything seemed to work fine until I updated the kernel. I'm not going to reinstall again (well, not right now) but, seems weird, that's all that I know I know. 

It's the same thing. I can ping myself, the router, but the moment i ping a site (google.ca) it errors out and freezes. I'm thinking it's a DNS issue, but how I don't know.

---

### Post by mips on 2005-11-28
What happens if you boot with a downgraded kernel ?

---

### Post by derrick1985 on 2005-11-30
[QUOTE=mips]What happens if you boot with a downgraded kernel ?[/QUOTE]
Nothing, same problem (just tried it twice)

Now i'm just running through my cable modem to see if it's a router issue, and so far it's been so good. Forgot how fast unshared connections were.

Anyways, i'll let you know how it goes. Right now, i'm testing with the latest kernel.

---

### Post by derrick1985 on 2005-12-01
Ok, i don't know what it is but I think i know where it is. I think it has something to do with the way Linux sends out requests for DNS information, but i'm not sure. The reason I say this is because the router works fine in Windows (same settings) and Linux, it freezes up every so often (new and old kernel) so the only thing I can think of is if there is a difference with how the two send/receive messages, it could be bogging down the router. 

Anybody have any ideas?

---

### Post by mips on 2005-12-02
Open your **/etc/resolv.conf** file.

In it you will find the line, **nameserver xxx.xxx.xxx.xxx** which corrosponds to your routers address. Remove that line or hash it out.
Get the DNS server addresses from your ISP, you can usually find it on their web support site or call them.

Add those two nameserver addresses to your resolve.conf file and see what happens.

---

