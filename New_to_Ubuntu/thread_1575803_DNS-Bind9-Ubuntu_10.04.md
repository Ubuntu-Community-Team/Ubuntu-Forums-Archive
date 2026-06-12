---
title: "DNS-Bind9-Ubuntu 10.04"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by pangeh on 2010-09-16
Hi,

I've just started using Ubuntu and am setting up a small office network. Right now I'm reading about Bind9 and setting up a DNS server using Ubuntu 10.04.

I've read through alot of the documentation and have even set up the server. When I tried again though it didn't work so will have to do some trouble shooting.

My question however is what is the actual difference between the Bind 9 config files? named.conf, named.conf.local and named.conf.options

Is there a document that gives first a general outline that specifically says which files configure Bind9 and what there specific purpose is?

I've been through alot of documentation and don't seem to be understanding it. Most of the searches I've done come up with articles and dont really explain anything.

Thanks in advance and apologies if this is a silly question however I would like to understand the different technologies so that I can use them properly.

Regards
p

---

### Post by CharlesA on 2010-09-16
Bind is a bit complicated to set up for a small network.

I would recommend dnsmasq, as it's small and easier to configure.

---

### Post by pangeh on 2010-09-16
Hi CharlesA,

Thanks for your response. Will have a look into DNS masq, it looks pretty interesting for basic use, I might use it for my home network. However the purpose of this post is to increase my understanding of BIND9. 

I did get a DNS server up and working by setting the zone files and configuring named.conf however when I rebuilt the server and did the same thing I ran into problems. So I wanted to know the difference between the config files for BIND9, their purpose and how they work.

The office is due to expand so having a fully functional DNS server(s) will be important in the future.

rgds
P

---

### Post by JKyleOKC on 2010-09-16
The named.conf file is the main configuration file, and is the only one that the DNS server actually calls. The other two are called by lines in named.conf itself, that start with the keyword "include" and which cause the specified file's content to be inserted at that point, at run time.

The purpose of this three-way division is to simplify your maintenance of the file, through updates and changes to your network. The "local" file is supposed to contain all of the information that's specific to your network, while the "options" file specifies the exact options that you want the server to use.

When the program is updated, either manually or through automatic updates, only the "named.conf" file is rewritten to reflect any changes. Updating the program does not change your "local" and "options" files, but any changes that you have made in "named.conf" itself will vanish without warning.

Such use of "included" local files is quite common in system configuration, and although it's a bit confusing when you first encounter it, really does help as time passes and one forgets all the little tweaks made to make things work in your own specific environment.

Hope this helps! The BIND system is a bit tricky to set up initially, but once it's properly configured works quite well and is almost maintenance-free.

---

### Post by pangeh on 2010-09-17
Hi Jim,

Thank you very much for your reply. That really helped clear some of my confusion. Will go and have another bash at creating a DNS server using a vm and see how I get on.

Thanks again.

Kind Regards
P

---

