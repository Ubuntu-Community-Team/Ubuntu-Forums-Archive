---
title: "Grab IP Address from DNS Name for smbfs"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by televisi on 2009-05-03
Hi All,
I have Ubuntu Server edition.

Is there any command to get IP address from DNS name/computer name?

I need this IP address to **mount -t smbfs //*_<IP Address>_*/** /<destination folder/

I've been using **sudo tracert <computer name> **but then it gives me all the hops detail...

Thanks

---

### Post by lorderico on 2009-05-03
Try nslookup

---

### Post by alphacrucis2 on 2009-05-03
> **televisi said:**
> Hi All,
I have Ubuntu Server edition.

Is there any command to get IP address from DNS name/computer name?

I need this IP address to **mount -t smbfs //*_<IP Address>_*/** /<destination folder/

I've been using **sudo tracert <computer name> **but then it gives me all the hops detail...

Thanks

dig is the command you need.

```
man dig
```

for explanation of the parameters,

---

### Post by televisi on 2009-05-03
Hi,
Thanks!
dig seems like a good tool, but I still can't get my Windows IP.

**$ Ping 192.168.1.8**
```
PING 192.168.1.8 (192.168.1.8) 56(84) bytes of data.
64 bytes from 192.168.1.8: icmp_seq=1 ttl=128 time=37.7 ms
64 bytes from 192.168.1.8: icmp_seq=2 ttl=128 time=25.9 ms
64 bytes from 192.168.1.8: icmp_seq=3 ttl=128 time=25.9 ms
64 bytes from 192.168.1.8: icmp_seq=4 ttl=128 time=25.9 ms

```

**$ dig XPCOMPNAME**
```

; <<>> DiG 9.4.2-P2 <<>> XPCOMPNAME
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

even with
**$ dig XPCOMPNAME -p 8080**
or **$ dig XPCOMPNAME -p 139**
```

; <<>> DiG 9.4.2-P2 <<>> XPCOMPNAME
;; global options:  printcmd
;; connection timed out; no servers could be reached

```

---

### Post by Alterax on 2009-05-04
Just ping your Windows machine's name to get the IP address:


EXAMPLE:  Pinging my imaginary desktop "pandora"

alterax@gulalev:~/Desktop$ ping pandora
PING pandora (192.168.2.30) 56(84) bytes of data.
64 bytes from pandora (192.168.2.30): icmp_seq=1 ttl=64 time=1.10 ms
64 bytes from pandora (192.168.2.30): icmp_seq=2 ttl=64 time=1.10 ms

gives me pandora's address in parentheses: 192.168.2.30


Or you could use the DNS name in place of the IP address in your command. DNS is there so you can use friendly names rather than IP addresses; it should resolve just fine.

---

### Post by televisi on 2009-05-04
Hi,
As I am willing to put this in script, I don't think I can get just the IP address from 'ping' command? unless I can make it "break" from pinging and grab the IP address only (using regex??)

The other thing is, I put all my Windows machines in Dynamic IP mode, which I can't set/guess which IP that use which name...

Thanks
> **Alterax said:**
> Just ping your Windows machine's name to get the IP address:


EXAMPLE:  Pinging my imaginary desktop "pandora"

alterax@gulalev:~/Desktop$ ping pandora
PING pandora (192.168.2.30) 56(84) bytes of data.
64 bytes from pandora (192.168.2.30): icmp_seq=1 ttl=64 time=1.10 ms
64 bytes from pandora (192.168.2.30): icmp_seq=2 ttl=64 time=1.10 ms

gives me pandora's address in parentheses: 192.168.2.30


Or you could use the DNS name in place of the IP address in your command. DNS is there so you can use friendly names rather than IP addresses; it should resolve just fine.

---

### Post by lavinog on 2009-05-04
try nmblookup XPCOMPNAME

see if this works too...i don't think it will, but worth a shot:
ping XPCOMPNAME.local

---

### Post by televisi on 2009-05-04
Yay, nearly there...
This is the result of doing nmblookup XPCOMPNAME
```

added interface ip=192.168.1.100 bcast=192.168.1.255 nmask=255.255.255.0
Socket opened.
querying XPCOMPNAME on 192.168.1.255
Got a positive name query response from 192.168.1.8 ( 192.168.1.8 )
192.168.1.8 XPCOMPNAME<00>

```

now, I can just grep it => **nmblookup XPCOMPNAME | grep "Got a positive name query"**

But by doing above command, it gives the appropriate line:
```
Got a positive name query response from 192.168.1.8 ( 192.168.1.8 )
```

Now...how do I **extract only IP address **out of that line?

> **lavinog said:**
> try nmblookup XPCOMPNAME

see if this works too...i don't think it will, but worth a shot:
ping XPCOMPNAME.local

---

### Post by lavinog on 2009-05-04
> **televisi said:**
> Hi,
As I am willing to put this in script, I don't think I can get just the IP address from 'ping' command? unless I can make it "break" from pinging and grab the IP address only (using regex??)

```
ping -c 1
``` can be used to limit it to a single ping

look at nmap also
there are a bunch of options for it but
```
nmap -sP 192.168.1.0/24
```
will give an output like this:
```

Starting Nmap 4.76 ( http://nmap.org ) at 2009-05-04 06:13 CDT
Host 192.168.1.1 appears to be up.
Host 192.168.1.100 appears to be up.
Host 192.168.1.102 appears to be up.
Host 192.168.1.106 appears to be up.
Nmap done: 256 IP addresses (4 hosts up) scanned in 3.90 seconds

```
Supposedly the latest nmap can be used to detect remote computers infected with the conficker virus.

---

### Post by lavinog on 2009-05-04
```
nmblookup XPCOMPNAME | grep "Got a positive name query"|cut -d '(' -f 2 |cut -d ')' -f 1
```
it will leave a space at the beginning and end though.
(I know someone is going to yell at me for not using awk)

---

### Post by televisi on 2009-05-04
Brilliant!!!
Thanks heaps lavinog, this **cut **command really a great command!!!

Furthermore, **nmap **is a good tool too, to find all IP address!!!

Thank you!!!

> **lavinog said:**
> ```
nmblookup XPCOMPNAME | grep "Got a positive name query"|cut -d '(' -f 2 |cut -d ')' -f 1
```
it will leave a space at the beginning and end though.
(I know someone is going to yell at me for not using awk)

---

### Post by lavinog on 2009-05-04
There used to be a way to make it all work by installing winbind and adding wins to the /etc/nsswitch.conf file. I don't know if that is still the case though. I don't have alot of windows computers on my networks anymore, but local name resolution was something that just worked on windows computers better than ubuntu.

---

### Post by lavinog on 2009-05-04
if you are scripting it you should store the greped output to a variable then test its length to ensure the host exists, prior to cutting
```

nmbstr=$(nmblookup XPCOMPNAME | grep "Got a positive name query")
[[ -z "$nmbstr" ]]||{
echo "no host"
exit
}
ipadd=$(echo "$nmbstr"|cut -d '(' -f 2 |cut -d ')' -f 1)
echo $ipadd

```

---

### Post by televisi on 2009-05-15
Thanks!, I modify your cut to omit prefix & suffix spaces:
```
ipadd=$(echo "$nmbstr"|cut -d '(' -f 2 |cut -d ')' -f 1) | cut -d ' ' -f 2 | cut -d ' ' -f 1

```

> **lavinog said:**
> if you are scripting it you should store the greped output to a variable then test its length to ensure the host exists, prior to cutting
```

nmbstr=$(nmblookup XPCOMPNAME | grep "Got a positive name query")
[[ -z "$nmbstr" ]]||{
echo "no host"
exit
}
ipadd=$(echo "$nmbstr"|cut -d '(' -f 2 |cut -d ')' -f 1)
echo $ipadd

```

---

