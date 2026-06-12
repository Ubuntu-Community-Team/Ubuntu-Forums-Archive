---
title: "View information being sent to internet"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by tdrusk on 2010-01-15
I just followed this guide. So far it works.
[http://www.livingubuntu.com/?p=3001](http://www.livingubuntu.com/?p=3001)

Now I just need proof that there is some encryption. How can I view what is being sent out?

---

### Post by MarkC502 on 2010-01-16
There are quite a few network monitoring applications in Linux :-) 

But the one you want is wireshark , as it has nice graphics and can show you all your packets in and out and you can do all sorts of neat geeky things with said packets :-)

COMMAND TO INSTALL

sudo apt-get -y install wireshark

It should then be under Applications -> Internet -> Wireshark


Have fun !

---

### Post by baddog144 on 2010-01-16
Yep, wireshark is definitely the best (imho).
Very neat and functional.

---

### Post by Cheesemill on 2010-01-16
That guide you've used will encrypt all of your internet traffic, but DNS requests will still be in plain text. This means that the hotspot will be able to see where you've been and possibly still block you from certain sites.

To get round this browse to about:config in Firefox and change the setting:
```
network.proxy.socks_remote_dns
```to true.

Now all your DNS requests will be sent along the SSH tunnel as well.


Edit - The guide you're using is wrong!
The command should be:
```
ssh -D 9999 user@serverip
```
where user@serverip is the username and address of the server you wish to tunnel through.

---

### Post by tdrusk on 2010-01-17
> **Cheesemill said:**
> That guide you've used will encrypt all of your internet traffic, but DNS requests will still be in plain text. This means that the hotspot will be able to see where you've been and possibly still block you from certain sites.

To get round this browse to about:config in Firefox and change the setting:
```
network.proxy.socks_remote_dns
```to true.

Now all your DNS requests will be sent along the SSH tunnel as well.


Edit - The guide you're using is wrong!
The command should be:
```
ssh -D 9999 user@serverip
```where user@serverip is the username and address of the server you wish to tunnel through.'

What about if I did System>preferences>network proxy and changed it there? I intend on encrypting all my activity anyway.

---

### Post by tdrusk on 2010-01-20
Can someone answer my previous question?

---

### Post by aldegaz on 2010-06-22
That guide is *not* wrong.

It is doing SSH via the localhost connection. When a user does

```

ssh localhost

```

The username is implied. If you still feel this is completely wrong, specify correctly why it is wrong.

So the above would be the same as:

```

ssh my_username@localhost
ssh my_username@127.0.0.1

```

---

### Post by aldegaz on 2010-06-22
@tdrusk:

The way you check if that is actually working is, after you tell Firefox to use the SOCKS proxy, try to browse around without running the SSH connection.

It should say that the Proxy is not working and should not display anything but that Firefox Error.

Then run again the SSH connection and try to reload those pages, you will see the sites should be loading.

This basically is proof that the packets are going through SSH.

Now, as far as actually "viewing" packets to verify encryption, any of the suggested tools should be good (e.g. wireshark)

---

