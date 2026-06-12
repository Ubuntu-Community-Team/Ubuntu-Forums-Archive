---
title: "Unable to connect through proxy server"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by dckirba on 2006-11-13
Hello all,

Our office just had a proxy server installed (I'm very clueless here so forgive me if I use the wrong terms).

After changing settings in Firefox and Opera I can connect to the internet fine, but I am unable to download packages or updates. I get an error connecting to the repository.

Where can I configure the proxy server settings for my system as a whole as opposed to configuring it individually for applications that access the web.

Thanks a lot,
Regards,
David

---

### Post by dckirba on 2006-11-13
Hey! I was looking through the administration menu and using the network tools, but all the time it was under preferences>network proxy!

Working fine now,

Cheers,
David K

---

### Post by jfenwick on 2006-11-14
Where do you set the proxy for apt at the command line?
I can use the Synaptic Package Manager but I'd rather use the command line if possible.

---

### Post by cjbmtb on 2006-11-17
In version Edgy - which I take you are using(?), there is no apt.conf in /etc/apt.

You can type the following from command line, though (where X.X.X.X is your proxy address and PN is the port number, most likely 80:

export http_proxy="http://X.X.X.X:PN"

Then run an apt command, such as:

apt-get upgrade

To enable this proxy arg permanently, you can place the entire export command on a line in your .bashrc in your home directory.

If you are using a version that contains an apt.conf file in /etc/apt, place this in the file (or edit the line to contain your proxy IP):

Acquire::http::Proxy "http://X.X.X.X:80"

---

