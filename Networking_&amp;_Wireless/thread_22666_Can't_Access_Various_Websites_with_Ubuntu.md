---
title: "Can't Access Various Websites with Ubuntu"
date: 2005-03-29
forum: Networking &amp; Wireless
---

### Post by Tet Omeg on 2005-03-29
Hello, I've mentioned my below problem in another thread, but since the below problem is off-topic to the title of that thread I thought it would be more appropriate to give it its own thread. I hope someone can help me with this problem.

Recently I'm finding it quite impossible to connect to the websites [http://www.anti-state.com](http://www.anti-state.com) , [http://www.antiwar.com](http://www.antiwar.com) , [http://www.somalianarchy.com](http://www.somalianarchy.com) , and [http://www.foranewliberty.com](http://www.foranewliberty.com) in Ubuntu (using either the Firefox or Opera 7.54u2 browsers in Ubuntu). All these websites have the same IP address: 72.3.135.33 . I have no problems accessing any other websites that I've tried in Ubuntu.

Yet I have absolutely no problem accessing those same websites on a different computer running Windows XP with either Opera, K-Meleon, or Maxthon using the same exact phone line (I simply disconnect the line from one computer and plug it into another), internet service provider, and ISP account.

What is even more weird about this is that I was able to connect to the anti-state.com website in Ubuntu a bit over two days or so ago, but ever since about the night before last I haven't been able to connect to that website in Ubuntu. And I've since learned that I am unable to connect to any of the other websites that I've tried which have the 72.3.135.33 IP address while using Ubuntu.

Like I said, I'm having no trouble whatsoever connecting to those websites using a different computer running Windows XP. I've been extensively testing this back and forth between computers so I know it's not just some random fluke.

What I can see happening (while running Ubuntu) is that Firefox will say "Resolving host www.anti-state.com" (or any of the other above-mentioned websites) and then very quickly after that it will say "Connecting to www.anti-state.com," but then nothing whatsoever happens after that. From the lights on my external modem I can see that no data is being transferred after it says "Connecting to www.anti-state.com" (other than a few quick blips every now and then, as if it's trying to establish a connection but isn't able to). It doesn't matter how long I wait, no data is ever transferred. The progress bar in Opera shows absolutely no data-transfer from any of the above-said websites--not so much as a single byte.

I did a ping on [www.anti-state.com](www.anti-state.com) and below is what the Terminal produced:

$ ping [www.anti-state.com](www.anti-state.com)
PING anti-state.com (72.3.135.33) 56(84) bytes of data.
64 bytes from antiwar.com (72.3.135.33): icmp_seq=1 ttl=49 time=205 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=2 ttl=49 time=161 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=3 ttl=49 time=174 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=4 ttl=49 time=168 ms
64 bytes from antiwar.com (72.3.135.33): icmp_seq=5 ttl=49 time=164 ms
...

---

And it just kept on going on like that. I shut it down when the "icmp_seq=" was up above 200.

I did a Wget on these websites, and below is the result:

$ wget [http://www.anti-state.com/index.php](http://www.anti-state.com/index.php)
--18:34:17-- [http://www.anti-state.com/index.php](http://www.anti-state.com/index.php)
=> `index.php'
Resolving [www.anti-state.com](www.anti-state.com)... 72.3.135.33
Connecting to [www.anti-state.com](www.anti-state.com)[72.3.135.33]:80...

---

It produces the same result for [http://www.anti-state.com/forum/index.php](http://www.anti-state.com/forum/index.php) , [http://www.antiwar.com](http://www.antiwar.com) , [http://www.somalianarchy.com](http://www.somalianarchy.com) , and [http://www.foranewliberty.com](http://www.foranewliberty.com) . It just gets to "Connecting to" and nothing else ever happens.

These are the only websites of all that I have tried wherein I am having this problem in Ubuntu. As I said, they all have the same IP address: 72.3.135.33 .

I would be very appreciative of any help anyone can offer me on this problem.

---

### Post by kassetra on 2005-03-29
Ok, I just tried accessing those sites and I seem to be able to just fine in Ubuntu with this version of Firefox:
(Ubuntu package 1.0-2ubuntu4-warty99)

Are you using the version of Firefox that came with Warty, or have you upgraded?

If you haven't upgraded, I suggest you add the backports repositories to your sources.list in Synaptic and upgrade your firefox to at least the version I have...

---

### Post by Tet Omeg on 2005-03-29
[QUOTE=kassetra]Ok, I just tried accessing those sites and I seem to be able to just fine in Ubuntu with this version of Firefox:
(Ubuntu package 1.0-2ubuntu4-warty99)

Are you using the version of Firefox that came with Warty, or have you upgraded?

If you haven't upgraded, I suggest you add the backports repositories to your sources.list in Synaptic and upgrade your firefox to at least the version I have...[/QUOTE]

It's not a problem with Firefox. As I said in my above post, I have Opera 7.54u2 installed in Ubuntu and it is unable to connect to any of those above-mentioned websites. As well, ping and wget are unable to connect to any of those above-mentioned websites.

---

### Post by kassetra on 2005-03-29
[QUOTE=Tet Omeg]It's not a problem with Firefox. As I said in my above post, I have Opera 7.54u2 installed in Ubuntu and it is unable to connect to any of those above-mentioned websites. As well, ping and wget are unable to connect to any of those above-mentioned websites.[/QUOTE]

Ok now that is just bizarre.  Let me think here.  

The only thing I can think of is that somehow, someway, you've blocked yourself access to that site...

Are you running a firewall in Ubuntu?

---

### Post by Tet Omeg on 2005-03-29
[QUOTE=kassetra]Ok now that is just bizarre.  Let me think here.  

The only thing I can think of is that somehow, someway, you've blocked yourself access to that site...
[/quote]

It's not just one website, but all websites that I've tried which have the 72.3.135.33 IP address, which covers four unique domain-names that I know of so far.

> 
Are you running a firewall in Ubuntu?

Yes, Firestarter 1.0.0. But even when I shut it completely down (even looking at the "All Processes" View in the System Monitor to make sure it is shut down) I am still unable to connect to any of those websites in Ubuntu.

---

### Post by Tet Omeg on 2005-03-29
I apparently fixed this problem. I reinstalled Ubuntu, but now that I think about it I'm not sure a reinstall was necessary.

I believe what might have been the problem is that I had originally used gnome-nettool (Computer > System Configuration > Networking) to set up the connection with my external modem, and when I did so I was having severe ultra-slow speed problems. I asked about this on this forum (see [http://www.ubuntuforums.org/showthread.php?t=22389](http://www.ubuntuforums.org/showthread.php?t=22389) ) and I was told to use wvdial instead, as gnome-nettool apparently often has problems with external modems.

But in using wvdialconf to configure the wvdial.conf file I left behind some of gnome-nettool's configurations already written to the /etc/wvdial.conf location in addition to adding wvdialconf's configurations. Atfer this was set-up with wvdial I was able to connect at a good speed, but possibly the other stuff in the configuration file screwed things up enough for the system to be confused when dealing with all the above-mentioned unique domain-names coming from the same IP address (i.e., 72.3.135.33 ). So this time I made sure to keep the wvdial.conf file squeaky-clean by only going with wvdialconf's configurations.

At least that is what I assume was probably the problem. At any rate, I can now visit all the above-mentioned websites with the 72.3.135.33 IP address.

---

### Post by Tet Omeg on 2005-03-29
[QUOTE=Tet Omeg]I apparently fixed this problem. I reinstalled Ubuntu, but now that I think about it I'm not sure a reinstall was necessary.

I believe what might have been the problem is that I had originally used gnome-nettool (Computer > System Configuration > Networking) to set up the connection with my external modem, and when I did so I was having severe ultra-slow speed problems. I asked about this on this forum (see [http://www.ubuntuforums.org/showthread.php?t=22389](http://www.ubuntuforums.org/showthread.php?t=22389) ) and I was told to use wvdial instead, as gnome-nettool apparently often has problems with external modems.

But in using wvdialconf to configure the wvdial.conf file I left behind some of gnome-nettool's configurations already written to the /etc/wvdial.conf location in addition to adding wvdialconf's configurations. Atfer this was set-up with wvdial I was able to connect at a good speed, but possibly the other stuff in the configuration file screwed things up enough for the system to be confused when dealing with all the above-mentioned unique domain-names coming from the same IP address (i.e., 72.3.135.33 ). So this time I made sure to keep the wvdial.conf file squeaky-clean by only going with wvdialconf's configurations.

At least that is what I assume was probably the problem. At any rate, I can now visit all the above-mentioned websites with the 72.3.135.33 IP address.[/QUOTE]

Nope, that's not what was causing the problem. I know now for sure what was causing the problem: it was the Firestarter firewall that was causing the problem.

After I reinstalled the Firestarter firewall I was no longer able to connect to any of the above-mentioned websites with the 72.3.135.33 IP address. Apparently even when I go into the "All Processes" View in the System Monitor to make sure it is shut-down, it still remains active. But by using the "Stop Firewall" button within Firestarter it will allow me to access the above-said websites.

For whatever reason, Firestarter will not allow access to any of the above-said websites with the 72.3.135.33 IP address when it is active.

---

