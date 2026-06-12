---
title: "VPN connection fails on 13.10 with &quot;invalid VPN secrets&quot; error"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by pvictory5 on 2013-12-13
After upgrading to Ubuntu 13.10 my VPN connection stated behaving erratically. I used to work ok in version 12.04, but after the upgrade I repeatedly get the "...invalid VPN secrets." error and the VPN fails to connect. I just have to retry 3 or 4 times in a row to get the VPN to connect successfully. This is without any changes to the VPN connection configuration or network manager restart.  
Just try to connect over and over again until it goes through.
This is a daily occurrence. 

It is getting tiresome to keep retrying until it connects. This worked like a charm before. :(
Since I don't have to actually change anything in the configuration to make it work (just be persistent and patient) it would seem something gets either cached or not released properly.

Also, is there a way to get the message to be more explicit as to what it failed?

Any help and ideas are welcomed!

---

### Post by Gustav_Toppa on 2014-02-26
I feel for the OP, as this is an infamous error, apparently due to an as-yet unfixed Gnome bug, which is all over the web, but, which nobody seems to know exactly why it happens, nor, more importantly, how to debug.
Nobody even seems to know WHAT a VPN secret is, in the first place!

If it helps the OP, I've tried EVERYTHING that is suggested on the web, as people aimlessly tried various and sundry remedies, and documented them all over here this week:
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

### Post by dan84 on 2014-04-17
this is the solution i used

As root edit /etc/NetworkManager/system-connections/vpn-connection-name and under [vpn], change the password flags line to:


password-flags=0


And add the following:
[vpn-secrets]
password=(your vpn password)

---

### Post by Amorget on 2014-04-20
> **dan84 said:**
> this is the solution i used

As root edit /etc/NetworkManager/system-connections/vpn-connection-name and under [vpn], change the password flags line to:


password-flags=0


And add the following:
[vpn-secrets]
password=(your vpn password)

This worked for me, too

---

### Post by hockeybum27 on 2014-05-29
I tried the above, with the following results; it is probably important to note that this Cisco VPN connection uses Group authentication (in addition to the regular username and login)
I have an the following in my [vpn] section:

```
[vpn]
NAT Traversal Mode=cisco-udp
ipsec-secret-type=save
IPSec secret-flags=1
xauth-password-type=save
Vendor=cisco
Xauth username=**********
IPSec gateway=***.***.***.***
DPD idle timeout (our side)=90
IPSec ID=*****[B]
Xauth password-flags=0
[/B]Perfect Forward Secrecy=server
IKE DH Group=dh2
Local Port=500

```

I tried setting the bolded entry above to 0, and also added the [vpn-secrets] section as described:

```
[vpn-secrets]
**password=***********

```

but not only did that not work, it caused another entry to be added to the [vpn-secrets] section:

```
[vpn-secrets]
password=*********
**Xauth password=*******
```
So:
1. Should I leave the first line (Xauth password-flags) alone, and add a NEW entry just called password-flags
2. Should I change my password entry in the [vpn-secrets] to Xauth password?

Thanks!

---

### Post by landstander on 2014-10-20
The suggestion in post#3 did not work for me, and in fact non of the solutions that I've been able to find so far on the web (when searching for invalid VPN secrets) have worked to solve this problem.

Also, storing passwords in readable plain text files on your computer can be considered a blatant violation of best security practices. ...and I guess thats stated as if anything is really secure any more... *sigh* :/

**[_UPDATE:_] The solution that worked for me.**
I discovered that some of the characters I was using for the VPN password were causing this error. Specifically I believe it may have been the forward slash character "/" that may have been causing the issue. I suspect this may have been the problem as a similar problem was solved by removing that character from my password for an academic account. If nothing else works to solve this issue, change your password so that it doesn't use any special characters at all (see this comic strip for more info: [http://www.xkcd.com/936/]("http://www.xkcd.com/936/")) and see if that helps. If that does the trick you could try adding back in one special character at a time until you get this error again, then just make a passphrase that doesn't use that character.
Here is an interesting passphrase generator: [http://www.fourmilab.ch/javascrypt/pass_phrase.html]("http://www.fourmilab.ch/javascrypt/pass_phrase.html"), there are many other online. Try any search engine to find them but ixquick or duckduckgo seem to be popular choices for keeping your searches private.

**_Note:_** Since this problem is very wide spread and small groups of people are having success with various proposed solutions with no solution working for everyone, it is definitely possible that simply changing the password to a passphrase that doesn't use special characters will not solve the problem. In that case you are back to square one and will have to find one of the many other solutions posted that seem to be hit or miss for most people until you find one or some combination thereof that works for you, and if you do find a solution that works, please post it someplace.

---

### Post by Arnold_Balliu on 2015-05-26
What worked for me is that I saw that I had this problem like this guy here:
[http://askubuntu.com/questions/579159/unable-to-load-vpn-connection-editor-in-ubuntu-14-04-lts](http://askubuntu.com/questions/579159/unable-to-load-vpn-connection-editor-in-ubuntu-14-04-lts)
Then I installed the software in the first and only answer (copy/paste).
Everything seemed to work fine.

---

