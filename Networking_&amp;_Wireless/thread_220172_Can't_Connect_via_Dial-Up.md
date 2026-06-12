---
title: "Can't Connect via Dial-Up"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by palsyboy on 2006-07-21
One of my friends lives outside of cable or DSL range and can't afford satellite broadband, so he's stuck with dial-up.  I recently switched him over to Kubuntu, but so far, we can't get him online.

After problems with a Winmodem, I bought him a [hardware modem](http://www.newegg.com/Product/Product.asp?Item=N82E16825137104), which was recognized just fine.  However, after following the [Dial-Up Wiki entry](https://help.ubuntu.com/community/DialupModemHowto#head-cdd16131926f734c4736b833b907c8fb24478187), I never got a successful connection to SBC.  Here's some of what happened:

Using Knet, I got the following error:
```
Knet could not fully execute the pppd process.
ppp modules are not loaded
```
It's also worth nothing that when trying to configure Knet, "Protocol to Use" is blank.

Using Kppp, I got the following error:
```
The pppd daemon died unexpectedly
Exit status:1
```
I also got some message about "The remote system is required to autheticate itself," but I couldn't find any suitable way to do so.

I also tried pppconfig via the command line, where I entered the modem as /dev/ttyS0.  I ended up with an error about PAP authentication.

I guess it's obvious that I'm having some error related to ppp, but I know nothing about it or what to do.  Any help would be greatly appreciated.

---

### Post by ringmaster on 2006-07-31
I am having the same issue on Dapper; I tried to connect using kppp but every time I get the error: pppd died "the peer needs to authenticate itself but doesn't have a password" or something similar.
I live in Spain, I select pap/chat; the modem is configured correctly (hardware modem) and after connecting to the server allways get the same message, no matter what I do.

________________
Excuse me for my english.

Please check this thread:
[http://www.ubuntuforums.org/showthread.php?t=192222&highlight=pppd+error](http://www.ubuntuforums.org/showthread.php?t=192222&highlight=pppd+error)

---

### Post by Thundernuts on 2006-07-31
Fellas its not you or your modems its seems to be KDE.  I love the desktop but every distro I have tried with a newer KDE enviroment just will not work.  
I have got the exact same message you fellas have with Mepis, PCLinuxOS, etc in which you dial with kppp.  But guess what? Every distro with GNOME has worked fine, also Puppy and DSL Linux's wvdial has worked.  Now I just use Ubuntu and install KDE with Synaptic and dial with GNOME Network Administration Tool which you can still use in KDE after its installed.  I have looked for an answer as to why on numerous forums but I can never find anyone who knows. Its sucks.  I love Linux but for us Dial Up users things are kinda difficult at times.

---

### Post by rafalr on 2006-08-02
Hi,

I have had the same problem in Poland and initially thought something is garbled at the telecom/internet supplier but now see it is software/system related stuff.

After some toggling I managed to get kppp connect - you need to unhash one entry which is actually advised not to be unhashed, I am not at my PC now so can vaguely remember this is some kppp config file - probably located at /etc - and the unhashed line is "#noauth".

But this is no good either, as after unhashing this entry kppp is then dead and not reacting when you need to terminate/close the connection.

But I disagree this is KDE/kppp problem - the gnome-ppp does not detect the modem at all (although it is properly detected by system and I can force launching a proper connecting via System / Network menu).

So far I am connecting simply by the System / Network menu interface but this is far from elegant/proper way.

Wonder if anubody has solved that ?
Rafal

---

### Post by Ptero-4 on 2006-08-14
It's not KDE fella. It's the /dev/ttyS0 device file. It's f*cked up.

---

### Post by zxee on 2006-08-14
You can try the latest point release of dapper-if you can get it because on my system at least gnome-ppp now works-it didn't with the final 6.06 release. 
Also the exit status 1 error can be resolved in kppp (often) by adding noauth as a special parameter. kppp has a way to do this but I don't use kde anymore so I can't give you complete details. You can also add noauth to /etc/ppp/options but that's not considered the right way to fix the problem. 
Finally check out the link in my sig for more dial up dapper help.

---

### Post by linuxa on 2006-08-15
Hi guys, I finally got my dial up going with "wvdial" and the Linuxant drivers. kppp is still a Work in Progress for me though.

The #noauth option that **rafair** mentioned is in:
/etc/ppp/peers/kppp-options 

I thoroughly recommend you guys to try wvdial.

This thread in my view is a must read for modem users:
[winmodem out of the box - is it possible?]("http://ubuntuforums.org/showthread.php?t=82608&highlight=kppp")

Good luck guys.

---

