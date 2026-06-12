---
title: "Firefox download manager times out, how to use wget or ???"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by cforput on 2010-04-05
I have a 1.15GB file I am trying to download from cnet. It is Microsoft's Streets & Trips 2009. My CD has a read failure on it so I need to download a trial version and then use my existing key to unlock it. As I said the file is 1.15GB. When I try using Firefox's download manager, it says it is complete but never even gets close to download the entire file. I get about 25MB. 

Here is the link to download the file I am trying to get. 

[http://download.cnet.com/Microsoft-Streets-amp-Trips/3000-2056_4-53961.html](http://download.cnet.com/Microsoft-Streets-amp-Trips/3000-2056_4-53961.html)

When you click on this, it takes you to a new page where the download starts (and then times out). On this second page is a link that allows you to manually start the download. If I right click this link and then go to a terminal and type: wget then paste the link, here is what is pasted:

*****************************************************************
toshiba:~$ wget [http://dw.com.com/redir?edId=3&siteId=4&oId=3001-2056_4-53961&ontId=2056_4&spi=35aaa12de93ff3eb7db7d8b51c76aee8&lop=txt&tag=idl2&pid=171788&mfgId=50119&merId=50119&pguid=gJTgLwoPjGAAAGuPzxsAAAA-&destUrl=http%3A%2F%2Fsoftware-files-l.cnet.com%2Fs%2Fsoftware%2F17%2F17%2F88%2FST_2009.exe%3Fe%3D1270462198%26h%3D6528a609befb927c5c8533f01882a273%26lop%3Dlink%26ptype%3D1901%26ontid%3D2056%26siteId%3D4%26edId%3D3%26spi%3D35aaa12de93ff3eb7db7d8b51c76aee8%26pid%3D171788%26psid%3D53961%26fileName%3DST_2009.exe](http://dw.com.com/redir?edId=3&siteId=4&oId=3001-2056_4-53961&ontId=2056_4&spi=35aaa12de93ff3eb7db7d8b51c76aee8&lop=txt&tag=idl2&pid=171788&mfgId=50119&merId=50119&pguid=gJTgLwoPjGAAAGuPzxsAAAA-&destUrl=http%3A%2F%2Fsoftware-files-l.cnet.com%2Fs%2Fsoftware%2F17%2F17%2F88%2FST_2009.exe%3Fe%3D1270462198%26h%3D6528a609befb927c5c8533f01882a273%26lop%3Dlink%26ptype%3D1901%26ontid%3D2056%26siteId%3D4%26edId%3D3%26spi%3D35aaa12de93ff3eb7db7d8b51c76aee8%26pid%3D171788%26psid%3D53961%26fileName%3DST_2009.exe)
[1] 5152
[2] 5153
[3] 5154
[4] 5155
[5] 5156
[6] 5157
[7] 5158
[8] 5159
[9] 5160
--2010-04-04 21:10:59--  [http://dw.com.com/redir?edId=3](http://dw.com.com/redir?edId=3)
[10] 5161
Resolving dw.com.com... [11] 5162
[2]   Done                    siteId=4
toshiba:~$ 216.239.113.95
Connecting to dw.com.com|216.239.113.95|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://dw.com.com/redir/redx/?edId=3](http://dw.com.com/redir/redx/?edId=3) [following]
--2010-04-04 21:10:59--  [http://dw.com.com/redir/redx/?edId=3](http://dw.com.com/redir/redx/?edId=3)
Reusing existing connection to dw.com.com:80.
HTTP request sent, awaiting response... 404 Not Found
2010-04-04 21:11:00 ERROR 404: Not Found.

^C
[1]   Exit 1                  wget [http://dw.com.com/redir?edId=3](http://dw.com.com/redir?edId=3)
[3]   Done                    oId=3001-2056_4-53961
[4]   Done                    ontId=2056_4
[5]   Done                    spi=35aaa12de93ff3eb7db7d8b51c76aee8
[6]   Done                    lop=txt
[7]   Done                    tag=idl2
[8]   Done                    pid=171788
[9]   Done                    mfgId=50119
[10]-  Done                    merId=50119
[11]+  Done                    pguid=gJTgLwoPjGAAAGuPzxsAAAA-
toshiba:~$ 
*******************************************************************

How do I dig through the long string I paste after my wget command to enter the actual URL of the file?

OR 

Is there a Firefox download utility add on I could install that would have some of the same failover stuff that wget has?

---

### Post by NightwishFan on 2010-04-05
Try "Downthemall" on Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

