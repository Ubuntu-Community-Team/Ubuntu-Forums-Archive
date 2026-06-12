---
title: "gkrellm problems!"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by gustolove on 2006-11-08
i have gkrellmd installed on the server box i am running in my house.

i had gkrellm installed on my machine.

i've configured the gkrellm config file to allow my ip of 192.168.1.66 a connection to it.

```
gust@*****:/home$ gkrellm -f -s 192.168.1.23 -P 19150
Broken server connection
gust@*****:home$

```

for some reason when i try to connect to monitor it that is what i get.
it may be something small and stupid that i missed but please help. this is really annoying me!

---

### Post by gustolove on 2006-11-08
someone please give me some help here :-P

---

### Post by julioromano on 2007-01-09
same problem for me.
using edgy ppc.

---

### Post by axcairns on 2007-06-09
Same problem. Both client and server are Feisty.

---

### Post by FAWTS on 2007-06-12
The same for me, the server is a dapper and the client is Feisty Feist...

---

### Post by thejubster on 2008-02-01
Try checking that you have allowed the correct hosts in /etc/gkrellm.conf . This is the section that you are after........
[FONT="Courier New"]

# List of hosts allowed to connect.  If no hosts are specified in a
# gkrellmd.conf file or on the command line, all hosts will be allowed.
#
allow-host      localhost
allow-host      127.0.0.1
allow-host  ::ffff:127.0.0.1
#allow-host     ::1
#allow-host     192.168.0.*[/FONT]

The default config is to allow connections only from the local machine.

You need to add a new line that either contains the ip address or hostname of the remote client machine (e.g. 192.168.0.1 or myhost.mydomain.tld) or a network range to allow more than one machine to connect (e.g. 10.10.0.* - this allows all hosts on the 10.10.0.x network)

:)

---

