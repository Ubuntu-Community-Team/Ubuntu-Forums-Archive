---
title: "update failed"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by spiepie on 2009-04-05
Hi I have installed Heron on both of our laptops but we have recently not been able to update. get this message on both 
which is rather strange

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

we can surf web ok 
any ideas please? thanks
SI

---

### Post by rhcm123 on 2009-04-05
> **spiepie said:**
> Hi I have installed Heron on both of our laptops but we have recently not been able to update. get this message on both 
which is rather strange

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

we can surf web ok 
any ideas please? thanks
SI

works fine for me, try again

---

### Post by hyper_ch on 2009-04-05
please issue
```

ping security.ubuntu.com

```
and post the output here.

---

### Post by spiepie on 2009-04-05
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=500 ttl=46 time=281 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=502 ttl=46 time=312 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=503 ttl=46 time=254 ms
  just a few lines

---

### Post by hyper_ch on 2009-04-05
should then work fine. try again to update

---

### Post by nandemonai on 2009-04-05
That looks like a funky dns issue, either that or you're using a local proxy?

---

### Post by halitech on 2009-04-05
> **spiepie said:**
> Hi I have installed Heron on both of our laptops but we have recently not been able to update. get this message on both 
which is rather strange

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.5_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

we can surf web ok 
any ideas please? thanks
SI

Can you load [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/) ??

I'm wondering why it says [color="red"]Could not connect to localhost:4001 (127.0.0.1)[/color]

---

### Post by Therion on 2009-04-05
Try using a different server.

---

### Post by nandemonai on 2009-04-05
> **halitech said:**
> Can you load [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/) ??

I'm wondering why it says [color="red"]Could not connect to localhost:4001 (127.0.0.1)[/color]

Likewise, something odd going on with dns or hosts file there...

---

### Post by Lunx on 2009-04-05
Been a heap of stuff posted about update errors of late and that localhost issue is involved in nearly all of them I've seen. As to a reason, or solution, I have absolutely no idea...

Edit: By solution, I meant for stopping it trying to connect local host. Obviously changing server will be solution to getting the updates...

---

### Post by llamabr on 2009-04-05
Those servers are getting hammered, as people switch to jaunty.  Try switching to a mirror closer to your home.

---

### Post by halitech on 2009-04-05
whats the output of running this in the terminal
```
cat /etc/hosts
```

---

### Post by spiepie on 2009-04-06
here it is
thanks 
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 where can i learn about this stuff? is there some help online that you know of
Si

---

### Post by spiepie on 2009-04-06
Those servers are getting hammered, as people switch to jaunty. Try switching to a mirror closer to your home.

how do i do that? i cant find an option in update manager.
thanks for your help
si

---

### Post by nandemonai on 2009-04-06
> **spiepie said:**
> here it is
thanks 
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 where can i learn about this stuff? is there some help online that you know of
Si

Complete hosts file should look something like this:

```
127.0.0.1	localhost
127.0.1.1	blackbox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Substitute blackbox with your machines hostname. You can find that out by typing:

```
$ hostname
```

in a terminal.

As far as learning about this stuff well the ubuntu guide is a good place to start. Perhaps the Linux Documentation Project too.

[http://ubuntuguide.org/](http://ubuntuguide.org/)
[http://tldp.org/](http://tldp.org/)

---

### Post by Lunx on 2009-04-06
> **spiepie said:**
> Those servers are getting hammered, as people switch to jaunty. Try switching to a mirror closer to your home.

how do i do that? i cant find an option in update manager.
thanks for your help
si

You can set your server preference by selecting **System --> Administration --> Software Sources **and on the first tab in the window that opens will be an option to select which server you want from a list of available mirrors. (You can also access this menu directly from Synaptic if you select **Settings --> Repositories **). Just make sure to hit the reload button after making any changes. Not sure what the situation is where you live, but I'm in Australia, and instead of just using Server for Australia, I point it at a particular mirror as my ISP is in partnership with them and I don't have any metering of downloads from there, so all my Ubuntu updates and downloads don't eat into my monthly quota. May be worth investigating if there's an option like that where you are.

---

### Post by spiepie on 2009-04-08
thanks that set me in the correct direction. chose the best mirror option and let it scan for me then reloaded in synaptic

thanks for all your help guys.....solved!

---

