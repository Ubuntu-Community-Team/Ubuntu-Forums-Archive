---
title: "hma open vpn - invalid vpn secret"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by jgw on 2013-10-04
I am now getting an "invalid vpn secrets" error message when I try and run my hma open vpn.  I think this has just started up.  I am running with 12.04.3   I have also searched for this error and, apparently it has something to do with the network-manager.  I have stopped, and started said network but it didn't help.  I have read several fixes but they seem to be 2 years or more old.  I am not sure which might apply to the current ubuntu.  

I would appreciate any help on this one so that I can get my vpn back up and running.

Thank you.............

---

### Post by Gustav_Toppa on 2014-02-26
I feel for the OP, as this is an infamous error, apparently due to an  as-yet unfixed Gnome bug, which is all over the web, but, which nobody  seems to know exactly why it happens, nor, more importantly, how to  debug.
Nobody even seems to know WHAT a VPN secret is, in the first place!

If it helps the OP, I've tried EVERYTHING that is suggested on the web,  as people aimlessly tried various and sundry remedies, and documented  them all over here this week:
**[Installing Ubuntu 13.10 client for free public person vpn server (VPN Reactor)]("http://ubuntuforums.org/showthread.php?t=2207653&highlight=vpn+secrets")**

Note: Other very similar Ubuntu threads (most either wholly unanswered or filled with shots-in-the-dark) appear to be:[URL="http://ubuntuforums.org/showthread.php?t=2193559"]
[/URL]   
[LIST=1]
[*][VPN connection fails on 13.10 with "invalid VPN secrets" error]("http://ubuntuforums.org/showthread.php?t=2193559"), by [**[COLOR=#000000]pvictory5[/COLOR]**]("http://ubuntuforums.org/member.php?u=1889945")[URL="http://ubuntuforums.org/showthread.php?t=2178660"]
[/URL]
[*][ hma open vpn - invalid vpn secret]("http://ubuntuforums.org/showthread.php?t=2178660"), by [**[COLOR=#000000]jgw[/COLOR]**]("http://ubuntuforums.org/member.php?u=382468")[URL="http://ubuntuforums.org/showthread.php?t=1933442"]
[/URL]
[*][ OpenVPN]("http://ubuntuforums.org/showthread.php?t=1933442"), by [**[COLOR=#000000]carranty[/COLOR]**]("http://ubuntuforums.org/member.php?u=1070930")
[*][openvpn - invalid secrets error]("http://ubuntuforums.org/showthread.php?t=2042922"), by [**[COLOR=#000000]qwertyjjj[/COLOR]**]("http://ubuntuforums.org/member.php?u=595620")[URL="http://ubuntuforums.org/showthread.php?t=1193786&highlight=vpn+secrets"]
[/URL]
[*][ Invalid VPN Secrets driving me mad!]("http://ubuntuforums.org/showthread.php?t=1193786&highlight=vpn+secrets"), by [**[COLOR=#000000]jegan21[/COLOR]**]("http://ubuntuforums.org/member.php?u=844963")[URL="http://ubuntuforums.org/showthread.php?t=1894345&highlight=vpn+secrets"]
[/URL]
[*][ Tried everything and still "No VPN secrets found!"\.]("http://ubuntuforums.org/showthread.php?t=1894345&highlight=vpn+secrets"), by [**[COLOR=#000000]koohyar[/COLOR]**]("http://ubuntuforums.org/member.php?u=1480348")[URL="http://ubuntuforums.org/showthread.php?t=991144"]
[/URL]
[*][ The VPN connection 'xxxxx' failed because there were no valid VPN secrets.]("http://ubuntuforums.org/showthread.php?t=991144"), & [The VPN connection 'xxxxx' failed because there were no valid VPN secrets.]("http://ubuntuforums.org/showthread.php?t=991144") by [**[COLOR=#000000]giesen2[/COLOR]**]("http://ubuntuforums.org/member.php?u=515664") [URL="http://ubuntuforums.org/showthread.php?t=1841925&highlight=vpn+secrets"]
[/URL]
[*][ "No VPN Secrets" + Not storing password]("http://ubuntuforums.org/showthread.php?t=1841925&highlight=vpn+secrets"), by                                                                                      [**[COLOR=#000000]HangukMiguk[/COLOR]**]("http://ubuntuforums.org/member.php?u=90235")
[*][OpenVPN fails with no valid secrets]("http://ubuntuforums.org/showthread.php?t=2097223"), by [**[COLOR=#000000]yedd[/COLOR]**]("http://ubuntuforums.org/member.php?u=1768570")
[*][Re: PPTP VPN connection is failed after awhile]("http://ubuntuforums.org/showthread.php?t=1428224&p=9189779#post9189779"), by [**[COLOR=#000000]demuxer[/COLOR]**]("http://ubuntuforums.org/member.php?u=926857")[URL="http://ubuntuforums.org/showthread.php?t=1881124&p=12599384#post12599384"]
[/URL]
[*][ Re: How to Connect to PrivateTunnel.com Service Under Ubuntu 11.10]("http://ubuntuforums.org/showthread.php?t=1881124&p=12599384#post12599384"), by [**[COLOR=#000000]xylo04[/COLOR]**]("http://ubuntuforums.org/member.php?u=453042")[URL="http://ubuntuforums.org/showthread.php?t=1815802&highlight=vpn+secrets"]
[/URL]
[*][ Invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1815802&highlight=vpn+secrets"), by [**[COLOR=#000000]Deathmoon[/COLOR]**]("http://ubuntuforums.org/member.php?u=179443")[URL="http://ubuntuforums.org/showthread.php?t=1528840&highlight=vpn+secrets"]
[/URL]
[*][ VPN PPTP 'No VPN secrets!']("http://ubuntuforums.org/showthread.php?t=1528840&highlight=vpn+secrets"), by [**[COLOR=#000000]newbiefly[/COLOR]**]("http://ubuntuforums.org/member.php?u=702573")[URL="http://ubuntuforums.org/showthread.php?t=1671130"]
[/URL]
[*][ invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1671130"), by [**[COLOR=#000000]haloflightleader[/COLOR]**]("http://ubuntuforums.org/member.php?u=544906")[URL="http://ubuntuforums.org/showthread.php?t=1655562"]
[/URL]
[*][ VPN - failed because of invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1655562"), by [**[COLOR=#000000]chuckNbanna[/COLOR]**]("http://ubuntuforums.org/member.php?u=458230")[URL="http://ubuntuforums.org/showthread.php?t=1530144"]
[/URL]
[*][ Getting "No valid secrets" when trying to connect]("http://ubuntuforums.org/showthread.php?t=1530144"), by [**[COLOR=#000000]jancogo[/COLOR]**]("http://ubuntuforums.org/member.php?u=484700")[URL="http://ubuntuforums.org/showthread.php?t=1595209"]
[/URL]
[*][ "No valid VPN Secrets"]("http://ubuntuforums.org/showthread.php?t=1595209"), by [**[COLOR=#000000]altjx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1005100")[URL="http://ubuntuforums.org/showthread.php?t=1600971"]
[/URL]
[*][ invalid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1600971"), by [**[COLOR=#000000]mogambo[/COLOR]**]("http://ubuntuforums.org/member.php?u=1168650")[URL="http://ubuntuforums.org/showthread.php?t=1532655"]
[/URL]
[*][ VPN Connection Error "no valid VPN secrets."]("http://ubuntuforums.org/showthread.php?t=1532655"), by [**[COLOR=#000000]Mega_Fauna[/COLOR]**]("http://ubuntuforums.org/member.php?u=232419")[URL="http://ubuntuforums.org/showthread.php?t=1307345"]
[/URL]
[*][ Ubuntu 9.10 - the vpn connection 'xxx' failed because there were no valid vpn secrets]("http://ubuntuforums.org/showthread.php?t=1307345"), by [**[COLOR=#000000]sweisler[/COLOR]**]("http://ubuntuforums.org/member.php?u=435730")[URL="http://ubuntuforums.org/showthread.php?t=1569357"]
[/URL]
[*][ There were no valid vpn secrets error from NetworkManger]("http://ubuntuforums.org/showthread.php?t=1569357"), by [**[COLOR=#000000]hq4ever[/COLOR]**]("http://ubuntuforums.org/member.php?u=26304")[URL="http://ubuntuforums.org/showthread.php?t=1179848"]
[/URL]
[*][ no valid VPN secrets]("http://ubuntuforums.org/showthread.php?t=1179848"), by [**[COLOR=#000000]DeViLDuD3[/COLOR]**]("http://ubuntuforums.org/member.php?u=832863")[URL="http://ubuntuforums.org/showthread.php?t=1215168"]
[/URL]
[*][ How I fixed my "invalid VPN secrets" problem]("http://ubuntuforums.org/showthread.php?t=1215168"), by [**[COLOR=#000000]Roadcrew[/COLOR]**]("http://ubuntuforums.org/member.php?u=574005")[URL="http://ubuntuforums.org/showthread.php?t=1316052"]
[/URL]
[*][ OpenVPN No Secrets error when connecting.]("http://ubuntuforums.org/showthread.php?t=1316052") by [**[COLOR=#000000]T3kG33k[/COLOR]**]("http://ubuntuforums.org/member.php?u=758662")
[/LIST]
 etc.

---

