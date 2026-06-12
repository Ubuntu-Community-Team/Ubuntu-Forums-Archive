---
title: "detects network, won't connect"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by skydiver|goose on 2008-07-21
title says it, I can detect the network in wifi-radar and network connections, but it refuses to connect whenever I try to. MAC filer, no WEP key. Works fine in Windows, just not in Ubuntu..

---

### Post by fmc6338 on 2008-07-21
I have the same problem, hope someone can help.

---

### Post by skydiver|goose on 2008-07-21
problem solved. thanks god for IRC support. I'll copy and paste the conversation, just look for "goose" "Johnny" and "wbmj"


<goose> does anyone know why ubuntu will detect wireless networks, but not connect to them?
<Johnny> if i dont store passwords id have 15+ or so id have to remember and i get them mixed up
* [marfusha_] has quit (Read error: 104 (Connection reset by peer))
* david_ (n=david@S0106001346a6ea25.vc.shawcable.net) has joined #ubuntu
* fred__ (n=fred@host-85-27-3-252.brutele.be) has joined #ubuntu
<webman> johnny: you can't, if the server uses https, then it is done for you, otherwise, you can't enter anything into the form or else it can be sniffed
<Johnny> goose, i had a similar problem it has something to do with nm-applet and network manager conflict i think
* renaudk||972 (n=kevin@bdv75-10-88-171-40-5.fbx.proxad.net) has joined #ubuntu
* fxcp_ has quit (Remote closed the connection)
<Johnny> cant remember what though
<goose> Johnny, do you remember how you fixed it? I have no idea what nm-applet is
* Drago84 (n=drago@82.91.252.128) has joined #ubuntu
<Drago84> net
* skurakai (n=skurakai@ip-82-209-44-42.customer.poda.cz) has joined #Ubuntu
<Johnny> i dont goose i sold that laptop to a friend sorry
<skurakai> hi i have trouble with Firefox.
* PorkCharSui (n=derek@c-76-20-12-12.hsd1.ca.comcast.net) has joined #ubuntu
* raven-san (n=ravendf@S0106001cf0549620.vs.shawcable.net) has joined #ubuntu
* PorkCharSui has quit (Client Quit)
<Johnny> nm-applet is the little applet on the bar for network manager
* Drago84 (n=drago@82.91.252.128) has left #ubuntu ("Sto andando via")
* muntrue has quit ("Leaving")
* _2 (n=root@dialup-4.226.138.238.Dial1.Dallas1.Level3.net) has joined #ubuntu
<goose> damn.. it originally worked straight off the install, but when I installed wifi-radar, it stopped working
<skurakai> i'am using windows profile on NTFS but FF on start send "Firefox cannot use the profile "Default" because it is in use."
* meoblast001 has quit ("Leaving")
* raven-san has quit (Client Quit)
<Johnny> how do i set up snort jmarsden ?
* evilbug has quit (Remote closed the connection)
<wbmj> goose: to use wifi-radar you need to edit /etc/interfaces
<goose> wbmj, I tried removing wifi-radar and it still wouldn't connect after I got rid of it
* ehc (n=evan@67-42-181-202.eugn.qwest.net) has joined #ubuntu
<goose> wbmj, detects fine and dandy, just doesn't connect
* janhaj (n=janhaj@77.48.161.16) has joined #ubuntu
* Ashex has quit (Remote closed the connection)
* micware (n=micware@alf94-11-82-247-5-85.fbx.proxad.net) has joined #ubuntu
* micware has quit (Remote closed the connection)
* dynamethod has quit (Read error: 110 (Connection timed out))
* awan (n=awan@61.8.74.114) has joined #ubuntu
* ^2mMy^ has quit (Read error: 110 (Connection timed out))
<janhaj> !list FloodBot3
<ubottu> Sorry, I don't know anything about list floodbot3
<Johnny> does it ever connect goose and then just stop suddenly?
* beezer has quit ("Ex-Chat")
* awan has quit (Client Quit)
* dany (n=dany@IGLD-84-228-83-250.inter.net.il) has joined #ubuntu
<goose> Johnny, nope, doesn't assign me an IP address at all
<jmarsden> Johnny: read the docs first.  [http://www.snort.org/docs/#docs](http://www.snort.org/docs/#docs)
* dhumphreys has quit ("Leaving")
<wbmj> goose: Do the connections have an icon next them
* lat (n=lat@125.162.205.66) has joined #ubuntu
* co0lingFir3 (n=co0lingF@e181022022.adsl.alicedsl.de) has joined #ubuntu
<goose> wbmj, not following you. what do you mean?
* co0lingFir3 (n=co0lingF@e181022022.adsl.alicedsl.de) has left #ubuntu
* marmelaati (i=myrtti@ubuntu/member/myrtti) has left #ubuntu ("http://xkcd.com/322 *kblam*")
* marmelaati (i=myrtti@ubuntu/member/myrtti) has joined #ubuntu
* defDfloyd has quit (Connection reset by peer)
<wbmj> goose: left click on the nm-applet... the dropdown menu should list available connections
* sCOTTo (n=scott@124-170-61-225.dyn.iinet.net.au) has joined #ubuntu
<dany> I have an odd problem with my sound. I don't really know how to put this into words, so bear with me. When I play an audio file, it seems as though there are missing channels\tracks, does this sound familiar to anyone?
<goose> wbmj, it only says "Manual configuration"
<goose> dany, are you using a laptop or a desktop?
* FuDGe2 has quit ()
<dany> Like, I can't hear the lead guitar something or something of that sort
<dany> goose, a desktop
* scheuing (n=scheuing@61.48.101.77) has joined #ubuntu
 dagar Daisuke_Ido Daisuke_Laptop dak Dalroth damaltor dandel dany DarkAudit darkdelusions darrend daurnimator Dave123 Dave2 daveshere DaveyJ david_ Dazedit 
* grek has quit (Read error: 110 (Connection timed out))
<slchen> hi all, Is there any command to determine the encoding of a text file under ubuntu?
* desti_T2 (n=desti@p5B01921A.dip0.t-ipconnect.de) has joined #ubuntu
* scheuing has quit (Read error: 104 (Connection reset by peer))
<goose> dany, I had a similar problem with an old laptop. I ended up just reformatting and slapping on a fresh install and that fixed it.. :/
<wbmj> goose: open System > Administration > Network and set your wireless connection to roaming
* magnetron has quit (Read error: 104 (Connection reset by peer))
<dany> goose, this IS a fresh install :)
* gardar is now known as gardar`afk
<_2> slchen file
* magnetron (n=magnetro@unaffiliated/magnetron) has joined #ubuntu
* pabl0_ has quit (Read error: 110 (Connection timed out))
* rubystallion (n=johannes@p5B3EF013.dip.t-dialin.net) has joined #ubuntu
* no1wantdthisname (n=slow4@pool-71-178-11-15.washdc.fios.verizon.net) has joined #ubuntu
<goose> wbmj, ok, done. How can I check to see if I have an IP assigned to my wireless?
<slchen> _2, I just get ISO-8859 , seems the UTF-8 encoding
* itai-michaelson (n=itai@116.226.192.110) has joined #ubuntu
* Ademan has quit (Read error: 110 (Connection timed out))
<wbmj> goose: now go to the nm-applet and see if you have a list of access points
<slchen> but the content I tested are GB2312 , Big5,
* skurakai (n=skurakai@ip-82-209-44-42.customer.poda.cz) has left #Ubuntu
<goose> wbmj, yes, I do. Only one, the network I'm hard wired into right now and trying to connect to wirelessly.
* Ademan (n=dan@h-68-164-170-6.snfccasy.dynamic.covad.net) has joined #ubuntu
<itai-michaelson> jmarsden, can i ask you some g4u questions?
* desti has quit (Read error: 60 (Operation timed out))
* janhaj has quit ("Ex-Chat")
<wbmj> goose: laptop?
* BuZZ-dEE has quit (Remote closed the connection)
<jmarsden> itai-michaelson: Go ahead.
* renaudk||972 has quit (Remote closed the connection)
* magnetron has quit (Read error: 104 (Connection reset by peer))
* magnetron (n=magnetro@unaffiliated/magnetron) has joined #ubuntu
<itai-michaelson> will g4u name the discs the same way ubuntu does?
* Wisteso has quit ("Ex-Chat")
<goose> wbmj, yep. I'm 30% done downloading a 700 mb file, so I'm a bit hesitant to unplug the ethernet and test it
<itai-michaelson> i'm afraid to get them wrong
<goose> wbmj, is there a terminal command I can execute to see if I have an IP assigned to my wireless?
<jmarsden> No, it runs netbsd underneath so uses its disk devcie names.
* eeewtcv has quit (Read error: 104 (Connection reset by peer))
* grek (n=lolitka@ip-89-174-125-9.multimo.gtsenergis.pl) has joined #ubuntu
<jmarsden> itai-michaelson: read the manual again, there is a command that lists devices...
* ionic has quit ("Ex-Chat")
<webman> goose: ifconfig -a will show all interfaces
<itai-michaelson> jmarsden, so how can i tell which is the target disc and which the source
<itai-michaelson> can i browse them somehow?
<wbmj> goose: ok when you finish download disconnect the hardwire and logout/in........should update nm-applet listings

---

### Post by DPic on 2009-02-18
>,<! I'm reposting with only the relevant conversation...

<goose> does anyone know why ubuntu will detect wireless networks, but not connect to them?
<Johnny> goose, i had a similar problem it has something to do with nm-applet and network manager conflict i think
<Johnny> cant remember what though
<goose> Johnny, do you remember how you fixed it? I have no idea what nm-applet is
<Johnny> i dont goose i sold that laptop to a friend sorry
<goose> damn.. it originally worked straight off the install, but when I installed wifi-radar, it stopped working
<wbmj> goose: to use wifi-radar you need to edit /etc/interfaces
<goose> wbmj, I tried removing wifi-radar and it still wouldn't connect after I got rid of it
<goose> wbmj, detects fine and dandy, just doesn't connect
<Johnny> does it ever connect goose and then just stop suddenly?
<goose> Johnny, nope, doesn't assign me an IP address at all
<wbmj> goose: Do the connections have an icon next them
<goose> wbmj, not following you. what do you mean?
<wbmj> goose: left click on the nm-applet... the dropdown menu should list available connections
<goose> wbmj, it only says "Manual configuration"
<wbmj> goose: open System > Administration > Network and set your wireless connection to roaming
<goose> wbmj, ok, done. How can I check to see if I have an IP assigned to my wireless?
<wbmj> goose: now go to the nm-applet and see if you have a list of access points
<goose> wbmj, yes, I do. Only one, the network I'm hard wired into right now and trying to connect to wirelessly.
<wbmj> goose: laptop?
<goose> wbmj, yep. I'm 30% done downloading a 700 mb file, so I'm a bit hesitant to unplug the ethernet and test it
<goose> wbmj, is there a terminal command I can execute to see if I have an IP assigned to my wireless?
<webman> goose: ifconfig -a will show all interfaces
<wbmj> goose: ok when you finish download disconnect the hardwire and logout/in........should update nm-applet listings

---

