---
title: "So weird..Can connect and navigate maybe one or two webpages"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by hollowtd on 2010-01-20
So I've got a Ralink 802.11 N Wlan usb wireless adapter and in Network Manager I can see my wifi signal. Also, I can connect to my wifi signal, 100% strength. However, I can only navigate to a couple of web pages using either Chrome or Firefox. I can navigate to google and Ubuntu forums, but then after a few pages I can't anymore. 

I got the Ralink USB device to work following somone's advice lastnight and changing the connections in the IPv4. That helped but still I can't go beyond a couple pages, if that. 

Any ideas?

Thanks

---

### Post by hollowtd on 2010-01-20
Maybe it's a preference setting?

---

### Post by fooman on 2010-01-20
is this using firefox?  if yes,  maybe check your proxy settings.  in the toolbar,  click edit > preferences > advanced tab > settings button

try "no proxy" or "use system proxy settings".  close firefox and reopen it...see if that helps.

---

### Post by saphil on 2010-01-20
are you able to ping anything outside your wireless network? 

```
$ ping yahoo.com
```

Why I ask is you might be just looking at cached pages.

---

### Post by cariboo on 2010-01-20
You more than likely have a dns problem, as saphil said. If you can't ping yahoo.com by name, try:

```
ping 209.131.36.159
```

If the above works, you definitely have a dns problem.

---

### Post by hollowtd on 2010-01-20
I've changed the settings to No Proxy (it was already on system proxy) and that didn't do the trick. 

I think it's ping-ing though when I tried yahoo. Here's what TErminal gave me:

terry@terry-laptop:~$ ping yahoo.com
PING yahoo.com (209.131.36.159) 56(84) bytes of data.
64 bytes from b1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.159): icmp_seq=1 ttl=51 time=695 ms
64 bytes from b1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.159): icmp_seq=2 ttl=51 time=685 ms
64 bytes from b1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.159): icmp_seq=3 ttl=51 time=721 ms
64 bytes from b1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.159): icmp_seq=4 ttl=51 time=750 ms
64 bytes from b1.[www.vip.sp1.yahoo.com](www.vip.sp1.yahoo.com) (209.131.36.159): icmp_seq=5 ttl=51 time=775 ms

---

### Post by hollowtd on 2010-01-20
Also, my internal wireless card works fine. Lastnight I changed the DNS to 208.67.220.220

---

### Post by hollowtd on 2010-01-20
Is there something else I might try? 

I know it's not just recalling cached pages because when I go to google, ie, I can type in random things and get hits. It seems like when I try to load a page with lots of info, like youtube or something, that it doesn't work and won't load the page, but just searches. Strange indeed.

---

### Post by hollowtd on 2010-01-20
I know it's not just recalling cached pages because when I go to google, ie, I can type in random things and get hits. It seems like when I try to load a page with lots of info, like youtube or something, that it doesn't work and won't load the page, but just searches. Strange indeed.
__________________

---

### Post by wojox on 2010-01-20
Scroll down to Solution [FOT005]: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

See if that helps.

---

### Post by hollowtd on 2010-01-20
I did that and set it to false, as it was true. That got the search bar to come up a bit but still can't open pages like youtube.com but can still search on google.com Weird indeed. Any other setting ideas?

---

### Post by buddyd16 on 2010-01-20
do you live in a house or an apartment? if apartment how many wireless networks appear in the network manager. I had a similar issue and it wound up being that all the wireless channels were just plain crowded causing intermittent connection drops. 

The only solution I found was to upgrade everything to wireless n which lucky for me is much less crowded in my apartment.

Edit: Just reread your first post were you say you are using a "n" adapter. Is your router broadcasting in "n" or is it "B"? If everything is "n" try adjusting the channel/frequency on your router. You also need to be sure that both your receiver and your router are using the same "n" spec.

---

### Post by hollowtd on 2010-01-20
The same USB adapter works great with my mac. I live in apt but there are only 2 signals. I'm in Costa Rica right now for a few months, and the singal is g I think but the adapter can pick up all signal types, gnb and all. I can load a page or two and then nothing, if the webpage is not too big?

---

### Post by hollowtd on 2010-01-21
What should have I written under the DNS section. I just put in the numbers a fella told me to put in a couple days ago. Will that make a difference? Also, if I can see and connect to the wifi box signal with my usb wifi adapter, that does mean I have the driver installed, correct?

---

### Post by fooman on 2010-01-21
> **hollowtd said:**
> Also, my internal wireless card works fine. Lastnight I changed the DNS to 208.67.220.220

that is one of the opendns servers....the other being: 208.67.222.222

here is info on setting up:

[https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)


[B]
[/B]

---

### Post by hollowtd on 2010-01-21
Cheers I'll follow that and see if it helps at all.

---

