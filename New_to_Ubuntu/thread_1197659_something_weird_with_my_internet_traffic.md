---
title: "something weird with my internet traffic"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-26
i've benn running iptraf and noticed a weird connection with a lot of traffic:
> rapidshare.de:www 
but i've never visited the site nor i ever downloaded a torrent
the only thing i did was to watch videos on youtube

some help to clear this out..?

---

### Post by billgoldberg on 2009-06-26
> **heyyy said:**
> i've benn running iptraf and noticed a weird connection with a lot of traffic:

but i've never visited the site nor i ever downloaded a torrent
the only thing i did was to watch videos on youtube

some help to clear this out..?

Rapidshare is a file hosting site.

Nothing to do with torrents.

---

### Post by reeseslover531 on 2009-06-26
are you connected or downloading something from rapidshare?

---

### Post by heyyy on 2009-06-26
> **reeseslover531 said:**
> are you connected or downloading something from rapidshare?

i dont think so 
the only thing i've been doing was to watch videos from youtube...
but it seems to have a lot of traffic from this site(rapishare) why?

---

### Post by keplerspeed on 2009-06-26
Traffic will mean you are downloading something. Close all browsers, does the traffic continue?

---

### Post by heyyy on 2009-06-26
> **keplerspeed said:**
> Traffic will mean you are downloading something. Close all browsers, does the traffic continue?

it seems that the connections is active when i am watching videos from youtube..
does rapidshare have anything to do with youtube?

---

### Post by decoherence on 2009-06-26
> **heyyy said:**
> it seems that the connections is active when i am watching videos from youtube..
does rapidshare have anything to do with youtube?

I don't think so...

Do you have the NoScript add-on installed for Firefox? If not, you might check it out. I'd be curious to see if this is an XSS attack or something... i'm paranoid, though, so it's probably something else...

---

### Post by heyyy on 2009-06-26
> **decoherence said:**
> I don't think so...

Do you have the NoScript add-on installed for Firefox? If not, you might check it out. I'd be curious to see if this is an XSS attack or something... i'm paranoid, though, so it's probably something else...

after some research it seems that
when im watching this [video]("http://www.youtube.com/watch?v=zdm1_PVsIKc&feature=quicklist") the server appears to be in germany with this specific ip: 74.125.39.100
and on iptraf i have traffic in:206.132.73.16
is this normal?
can someone please help me understand

---

### Post by Jabz.biz on 2009-06-26
I cannot reproduce this problem just because I'm watching this video. Must be something else. Also: I cannot find any scripts on the youtube page that could trigger this.

---

### Post by heyyy on 2009-06-26
> **Jabz.biz said:**
> I cannot reproduce this problem just because I'm watching this video. Must be something else. Also: I cannot find any scripts on the youtube page that could trigger this.

maybe is this happening because im located in europe? or this isn't possible?

---

### Post by t0p on 2009-06-26
> **heyyy said:**
> after some research it seems that
when im watching this [video]("http://www.youtube.com/watch?v=zdm1_PVsIKc&feature=quicklist") the server appears to be in germany with this specific ip: 74.125.39.100
and on iptraf i have traffic in:206.132.73.16
is this normal?
can someone please help me understand

Youtube videos are not all hosted on youtube's own servers.  For instance, I often watch vids that are actually coming from google video servers.

My guess is that the vids you're watching are hosted on the rapidshare.de servers.

If you're still worried, I suggest you install a packet sniffer (eg [wireshark]("http://www.wireshark.org"), which is available through apt-get/Synaptic) and use it to discover what kind of traffic is coming and going from your computer.  I'm no expert, but I'll help you look at the packets if you like.  If you want an expert's help, I'm sure one of the forum members is a packet-sniffing guru.

But don't just post packets in the forum!  They may contain info that you'd rather keep private.

---

### Post by heyyy on 2009-06-26
> **t0p said:**
> Youtube videos are not all hosted on youtube's own servers.  For instance, I often watch vids that are actually coming from google video servers.

My guess is that the vids you're watching are hosted on the rapidshare.de servers.

If you're still worried, I suggest you install a packet sniffer (eg [wireshark]("http://www.wireshark.org"), which is available through apt-get/Synaptic) and use it to discover what kind of traffic is coming and going from your computer.  I'm no expert, but I'll help you look at the packets if you like.  If you want an expert's help, I'm sure one of the forum members is a packet-sniffing guru.

But don't just post packets in the forum!  They may contain info that you'd rather keep private.

i'd like to try it out but i have absolutely no expierience with this stuff i would like to have a step by step guidance on this

---

### Post by t0p on 2009-06-26
I decided to check out where connections were coming from whilst watching the video in question. So, I played the vid and entered into a terminal

```
netstat -a
```

This is a partial output:

> t0p@ubunty:~$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      

[...]
                     
tcp        0      0 ubunty.local:38752      wy-in-f100.google.c:www ESTABLISHED
tcp        0    586 ubunty.local:57320      warez.atman.pl:9001     ESTABLISHED
tcp        0      0 ubunty.local:41231      trusted.lostinthe:https ESTABLISHED
tcp        0      0 ubunty.local:34689      208.117.252.37:www      ESTABLISHED
tcp        0      0 ubunty.local:45459      74.125.105.227:www      ESTABLISHED
tcp        0      0 ubunty.local:34892      tor-proxy-2.cyphe:https ESTABLISHED

[...]


Some of these belong to youtube and google, which is hardly surprising.  But I haven't a clue who warez.atman.pl belongs to, nor why I'm connected with them while watching a youtube video.  Elsewhere in the output (which I haven't quoted above) was a connection with Telekom Malaysia Berhad.  I live in the UK, so I don't know what I'm doing with a Malaysian telecoms company.

Later on I'm going to re-run the vid and capture the traffic with wireshark.  I'm not really worried about this, but I am curious.

---

### Post by lovinglinux on 2009-06-26
> **Jabz.biz said:**
> I cannot reproduce this problem just because I'm watching this video. Must be something else. Also: I cannot find any scripts on the youtube page that could trigger this.

Neither do I.

---

### Post by lovinglinux on 2009-06-26
> **t0p said:**
> I decided to check out where connections were coming from whilst watching the video in question. So, I played the vid and entered into a terminal

```
netstat -a
```

This is a partial output:



Some of these belong to youtube and google, which is hardly surprising.  But I haven't a clue who warez.atman.pl belongs to, nor why I'm connected with them while watching a youtube video.  Elsewhere in the output (which I haven't quoted above) was a connection with Telekom Malaysia Berhad.  I live in the UK, so I don't know what I'm doing with a Malaysian telecoms company.

Later on I'm going to re-run the vid and capture the traffic with wireshark.  I'm not really worried about this, but I am curious.

I only get Google addresses. I'm in Brazil if that matters.

---

### Post by The Cog on 2009-06-26
**sudo netstat -pt**
will also tell you which application is holding the connection.

---

### Post by heyyy on 2009-06-27
> **t0p said:**
> I decided to check out where connections were coming from whilst watching the video in question. So, I played the vid and entered into a terminal

```
netstat -a
```

This is a partial output:



Some of these belong to youtube and google, which is hardly surprising.  But I haven't a clue who warez.atman.pl belongs to, nor why I'm connected with them while watching a youtube video.  Elsewhere in the output (which I haven't quoted above) was a connection with Telekom Malaysia Berhad.  I live in the UK, so I don't know what I'm doing with a Malaysian telecoms company.

Later on I'm going to re-run the vid and capture the traffic with wireshark.  I'm not really worried about this, but I am curious.

post the results plz

---

### Post by hovzio on 2009-06-27
I can't imagine rapidshare is hosting youtube videos.. Of course some videos on youtube are being hosted by google. GOOGLE is youtube... but then again i may be wrong. Rapidshare is a there for filetransfer. Like mentioned above, fire up wireshark and take a look at things.. First I would check to see, "am I downloading or uploading, how much when and where?" With wireshark you can recreate the whole conversation as long as no https or encryption is involved, which I doubt.  If there is alot of data being transfered and is encrypted; there is reason to investigate..

If you are uploading serious data to rapidshare there may be reason to worry, this could semi anonomys way to export data from a maschine, well easy to recover anonomously at least. I seriously doubt this though. The first step is finding out if there really is a data transfer going on. Do you have and funny repos installed?

---

### Post by heyyy on 2009-06-27
> **hovzio said:**
> I can't imagine rapidshare is hosting youtube videos.. Of course some videos on youtube are being hosted by google. GOOGLE is youtube... but then again i may be wrong. Rapidshare is a there for filetransfer. Like mentioned above, fire up wireshark and take a look at things.. First I would check to see, "am I downloading or uploading, how much when and where?" With wireshark you can recreate the whole conversation as long as no https or encryption is involved, which I doubt.  If there is alot of data being transfered and is encrypted; there is reason to investigate..

If you are uploading serious data to rapidshare there may be reason to worry, this could semi anonomys way to export data from a maschine, well easy to recover anonomously at least. I seriously doubt this though. The first step is finding out if there really is a data transfer going on. Do you have and funny repos installed?

i've never visited rapidshare

---

### Post by heyyy on 2009-06-27
can someone help me to use wireshark to check the connection

---

### Post by hovzio on 2009-06-27
> **heyyy said:**
> i've never visited rapidshare

I understood that, I've never visited doubleclick.net but still; its there... 

To sum it up, find out if your uploading data, that would not be a pretty scenario.

EDIT: Wireshark is not really a quick walkthrough:

[http://wiki.wireshark.org/](http://wiki.wireshark.org/)

And a nmap run through couldnt harm, check out nmap and zenmap. This will jujst let you know whats going on on your lan. May have little to do with rapidshare but its advisable to do this perodically for security sake.

---

### Post by t0p on 2009-06-27
I set out to do a bit of packet-capturing today.  But first I played the vid and used netstat to check if the suspicious traffic was at it again. And it wasn't: all I could see was google-related hosts.

Weird.  But there it is.

---

