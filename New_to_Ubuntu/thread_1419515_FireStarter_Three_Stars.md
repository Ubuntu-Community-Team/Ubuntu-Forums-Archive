---
title: "FireStarter: Three Stars?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by clymir on 2010-03-01
I love ubuntu, please understand,
 but when I saw firestarter had three stars
 in the "available applications" list,
 I installed it. THEN I had troubles,
 THEN I find people saying here:
 "its depreciated",
 "its no longer supported"
 "its a dead project" etc.

 As long as it's being offered on the mirors, I wonder
 does anyone know the reason that **FireStarter**,
 a Linux firewall, has
 **blocked live websites by default**?

 Is this indicitive of a virus?

 For example
comparing the fs "non-routables"
 to [IANA allocations]("http://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xml") :


 /etc/firestarter/non-routables [with allocations noted by me *  *  *  *  * ]
 (from FS 1.03 I assume -- running 8.04.4 LTS ):

> 0.0.0.0/8
1.0.0.0/8 *  *  *  *  *  whois.apnic.net
2.0.0.0/8 *  *  *  *  *  whois.ripe.net (Europe /Middle East /Central Asia)
5.0.0.0/8
7.0.0.0/8
10.0.0.0/8
23.0.0.0/8
27.0.0.0/8 *  *  *  *  *  whois.apnic.net (Asia /Pacific)
31.0.0.0/8
36.0.0.0/8
37.0.0.0/8
39.0.0.0/8
42.0.0.0/8
49.0.0.0/8
50.0.0.0/8 *  *  *  *  *  whois.arin.net (American)
100.0.0.0/8
101.0.0.0/8
102.0.0.0/8
103.0.0.0/8
104.0.0.0/8
105.0.0.0/8
106.0.0.0/8
107.0.0.0/8 *  *  *  *  *  whois.arin.net
108.0.0.0/8 *  *  *  *  *  whois.arin.net
109.0.0.0/8 *  *  *  *  *  whois.ripe.net
110.0.0.0/8 *  *  *  *  *  whois.apnic.net
111.0.0.0/8 *  *  *  *  *  whois.apnic.net
112.0.0.0/8 *  *  *  *  *  whois.apnic.net
113.0.0.0/8 *  *  *  *  *  whois.apnic.net
114.0.0.0/8 *  *  *  *  *  whois.apnic.net
115.0.0.0/8 *  *  *  *  *  whois.apnic.net
127.0.0.0/8
169.254.0.0/16
172.16.0.0/12
173.0.0.0/8 *  *  *  *  *  whois.arin.net
174.0.0.0/8 *  *  *  *  *  whois.arin.net
175.0.0.0/8 *  *  *  *  *  whois.apnic.net
176.0.0.0/8
177.0.0.0/8
178.0.0.0/8 *  *  *  *  *  whois.ripe.net
179.0.0.0/8
180.0.0.0/8 *  *  *  *  *  whois.apnic.net
181.0.0.0/8
182.0.0.0/8 *  *  *  *  *  whois.apnic.net
183.0.0.0/8 *  *  *  *  *  whois.apnic.net
184.0.0.0/8 *  *  *  *  *  whois.arin.net
185.0.0.0/8
186.0.0.0/8 *  *  *  *  *  whois.lacnic.net (Latin America /Caribbean)
187.0.0.0/8 *  *  *  *  *  whois.lacnic.net
192.0.2.0/24
192.168.0.0/16
197.0.0.0/8  *  *  *  *  *  whois.afrinic.net (Africa /Indian Ocean)
198.18.0.0/15
223.0.0.0/8
224.0.0.0/3
strange 044/8 ISN'T blocked, nor a ton of others

---

### Post by k3lt01 on 2010-03-02
Firestarter hasn't been supported in years so, to me at least, it stands to reason that it won't block many things that maybe it should if it was still supported.

You would be better learning how to use ipTables through UFW and its GUI GUFW if you want a firewall enabled.

P.S. This isn't a criticism so I hope you don't take it that way. When quoting something or posting code it saves a lot of space if you put it in a quote/code box.

---

