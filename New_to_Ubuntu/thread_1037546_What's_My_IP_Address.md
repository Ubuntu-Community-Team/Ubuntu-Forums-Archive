---
title: "What's My IP Address?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Drubie on 2009-01-11
Prepare to digress for a moment with a noobish question:

How do I find my IP address?  I bet it is a simple terminal command...

Man, I feel silly; thanks for putting up with me!

---

### Post by taurus on 2009-01-11
Does it connect directly to the net or through a router?

```
/sbin/ifconfig
```

---

### Post by spcwingo on 2009-01-11
type in the terminal:

```
ifconfig | grep inet
```

It's the first line, similar to this:

```
inet addr:192.168.0.102
```

I hope this gets the job done for you.

---

### Post by tuxxy on 2009-01-11
It is more simple to check your external IP using a website dedicated to this service, there are ways to check from the terminal but they usually involve one of these mentioned services.

The following is what I use in my COnky script and works fine :)

```
wget -qO - http://myip.dk/ | egrep -m1 -o '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}'
```Other methods are mentioned in the article below;

[http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html](http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html)[]("http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html")

---

### Post by Merkyor on 2009-01-11
this website will tell you your external ip

[http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by tuxxy on 2009-01-11
> **spcwingo said:**
> type in the terminal:

```
ifconfig | grep inet
```It's the first line, similar to this:

```
inet addr:192.168.0.102
```I hope this gets the job done for you.

I think he means his external IP, inet addr: would be his network IP.

---

### Post by Drubie on 2009-01-11
Yeah, I do need the external IP - thanks, I almost ran off with the wrong one...

---

### Post by Drubie on 2009-01-11
> **Merkyor said:**
> this website will tell you your external ip

[http://www.whatismyip.com/](http://www.whatismyip.com/)

rofl, so simple.  duh, why didnt I think of googling it...

---

### Post by tuxxy on 2009-01-11
> **Drubie said:**
> Yeah, I do need the external IP - thanks, I almost ran off with the wrong one...

hehe ye I thought you wanted the external, glad it worked anyway :)

---

