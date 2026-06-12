---
title: "Total Newbie to configue caching, forwarding DNS server using BIND"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by cschneider77 on 2011-03-19
Hello community,
    As stated in the title, I'm a two-day-old newbie to Ubuntu and to Linux. I am almost ready to sit for ICND2 (CCNA) so I am familiar with Cisco IOS CLI, but this Linux stuff is confusing me. Two days ago I was thrust into a project:
To get BIND running as a caching and forwarding DNS server. It must forward to servers at OpenDNS and/or Google. I must show evidence of it resolving a public FQDN (output from DIG is preferred). And I must provide the content of any configuration file I had to edit or create.
I have found most of the major configurations needed to complete the assignment, however, I don't know the simplest of commands to connect the dots, so to speak. So far, the things I know that I don't know are:
>how to uncomment in gedit
>how to save a configuration so that I can come back to it after eating, walking the dogs, etc.
>how to save the terminal session output to something like notepad
 
To elaborate on my ignorance of Linux, I don't understand why a new terminal window pops open when I enter the following command:
sudo gedit /etc/bind/named.conf.options
also, I don't know what to do after I edit the relevent information within that second terminal window. As you all can see, I need help with those basic commands that you all assume everyone should know. Thanks for any help.
cs

---

### Post by cariboo on 2011-03-20
Are you sure that isn't just a text editor that opens when you run the command?

I don't need or run bind, but usually when you make configuration changes to a service, you need to restart it. You can do it the Windows way by rebooting, or the Linux way by just restarting the service.

```
sudo /etc/init.d/bind restart
```

---

