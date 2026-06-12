---
title: "Ubuntu Server 10.1 Help"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by theunionstreet on 2010-10-28
Hello, so I am new to linux and trying to set up a home server. 
I can ssh to my server from my local network no problem but cannot seem to set it up so I can ssh from a non-local network.

What I have done so far:
1. Installed Ubuntu Server 10.10
    - Server detected DHCP settings and installed without error.

2. Edited my /etc/network/interfaces file to look like the following (for a static IP):
    # This file describes the network interfaces available on your system
    # and how to activate them. For more information, see interfaces(5).

    # The loopback network interface
    auto lo
    iface lo inet loopback

    # The primary network interface 
    auto eth0
    iface eth0 inet static
          address 192.168.2.15
          netmask 255.255.255.0
          network 192.168.2.0
          broadcast 192.168.2.255
          gateway 192.168.2.1

3. Edited the /etc/resolv.conf file:
    - I edited the nameserver: <IP HERE>
    - Am I supposed to put my local server ip here (192.168.2.15) or my network ip    address?      

4. I went into my router settings and port forwarded to my network (I tried port 80 and 21 I think)                     

Problem: So i have my neighbors wifi password so I can test to see if I can ssh from a non-local network from my house. I know that 192.168.2.15 is my local network address so I have been trying ssh username@mynetworkip (not the local one). I have not yet been successful in accessing my server from a non-local network. Am I on the right track? 

Thanks for your help,
Adam

---

### Post by theunionstreet on 2010-10-28
Oh yea, this is what my resolv.conf file currently looks like:

nameserver 98.247.241.76
domain Belkin
search Belkin

---

### Post by janpol on 2010-10-28
You are confusing private and public IP addresses. You can't point to one of your local IP's directly from the outside since private IP's are non routable. 

You need to do the following:

1. Redirect port 22 (since is the default port for ssh, if you changed it, use the port number you configured on the server) from your router to the local IP of the server(192.168.2.15 in this case). If you specify your router model or give me a screenshot of the config screen I can point you in the right direction. 

2. Find out the public address of your router, for that you can go here from any of the PC's connected to the router:

[http://www.whatsmyip.org/]("http://www.whatsmyip.org/")

3. Try to connect from the outside with ssh username@publicip

One more thing, the /etc/resolv.conf file is used to list the nameservers (DNS servers), so, if you don't need any custom DNS server just use some public DNS server like google's. Edit your resolv.conf file and place the following:

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Hope it helps

---

### Post by janpol on 2010-10-28
> **theunionstreet said:**
> Oh yea, this is what my resolv.conf file currently looks like:

nameserver 98.247.241.76
domain Belkin
search Belkin

So, you have your own custom domain, OK leave resolv.conf that way. Does that server resolvs DNS queries correctly? If it doesn't, you can add Google's public DNS for that (if you want that to happen ofc).

Still, this doesn't affect your ssh connection so it doesn't matter. But I'm curious, what do you want resolv.conf for? If you want to mount a DNS server and be able to acces it from the outside (so you can resolv your domain) you can't do it that way.

---

### Post by theunionstreet on 2010-10-28
You rule sir! I read somewhere to use port 21 and I thought that sounded a little off. I tried port 80 because that's what my router settings suggested for servers. 

Anyway, worked like a charm.

---

### Post by theunionstreet on 2010-10-28
So now that I have this server up and running, if I write a web page on it, how would I access this page through a web browser?

I linked my server to a dyndns page so now I can ssh to it (non-local) via: 
ssh <snip>

Should I create a new user that doesn't have admin rights?
So would the url be monkeytree.dyndns.org/~username?

---

### Post by janpol on 2010-10-28
You need to set up an Apache server (there are tons of information in google), redirect port 80 to your server (like you did with port 22) and then you will be able to acces your web page using the url monkeytree.dyndns.org. Port 80 is the standard port for web servers. When you write an url in your browser, it tries to connect to port 80 on that server.

I suggest you to read about Apache, try to set it up, and then come back here (create a new thread) if you have any questions.

Good Luck!

---

### Post by theunionstreet on 2010-10-28
Awesome. You gave me plenty to go on. I think I can problem solve from here. Thank you again.

---

### Post by CharlesA on 2010-10-28
I edited your above post to remove the SSH info. Don't want to have anyone trying to bruteforce their way into yer server.

As for using a different account for ssh access, I just use my normal account (which is part of the admin group) since you'd need to use sudo to do admin tasks.

---

### Post by ArgusVision on 2010-10-28
Since you said you are new. You might want to check out webmin. [www.webmin.com](www.webmin.com)  It makes a lot of tasks simpler and gives you a remote web based "GUI" of sorts. 
There are some advantages to learning to manage your server via command line only. If you can SSH and know what you're doing it's hard for anyone to take that from you.

---

