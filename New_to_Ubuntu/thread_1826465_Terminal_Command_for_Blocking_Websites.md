---
title: "Terminal Command for Blocking Websites"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by Pyprokid on 2011-08-16
Hello. 

I was wondering if there was a command on the terminal to not allow the computer to connect to certain websites, and if so, what is the command to re-establish connection?

Respectfully, 
Matt

---

### Post by decoherence on 2011-08-16
To block a specific site (rather than an entire domain) you're going to want to edit your firewall rules. I'm not sure if Ubuntu's Uncomplicated Firewall is up to the task.

If you want to block an entire domain, edit your /etc/hosts file

Type 'gksudo gedit /etc/hosts'

on the line that says '127.0.0.1' append the domain you want to block. For instance,

127.0.0.1 localhost slow.adserver.com

at least, you used to be able to do this. Maybe network manager will clobber it now. What it actually does is point that domain name at your own computer, effectively blocking it (though perhaps resulting in interesting behaviour if you run your own web server)

---

### Post by AlphaLexman on 2011-08-16
Well, the internet does not come from the terminal...
However it does come from your modem or router...
I doubt your modem or router have linux specific command line tools to control them.
They are most likely controlled from a web browser.
From there, you would have to setup web filters on either your modem or router.

Regards.

**EDIT:** posted seconds behind decoherence!

---

### Post by scorp123 on 2011-08-16
> **Pyprokid said:**
>  I was wondering if there was a command on the terminal to not allow the computer to connect to certain websites

You mean like some form of parental control? One really simple way to achieve that (= blocking of certain web sites) is to modify your local "hosts" file and have the web sites point to an illegal IP address. The file is usually located here: **/etc/hosts** ... and you need to be the super-user **"root"** to modify that file, so you will have to use the **"sudo"** command + a command line editor (vi, vim, nano, ...) to edit it.

Assuming you want to use "nano" (because it is relatively simple to use) you would use this command:
```
sudo nano /etc/hosts
```

The content of the file should look something like this:
```
192.168.1.1	yourhostnamehere	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	yourhostnamehere	localhost6.localdomain6	localhost6
127.0.1.1	yourhostnamehere

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```

Press enter a few times at the end of the file and now add your own entries of undesired web sites so that the file looks like as shown below. The IP adress "**0.0.0.0**" (usually used to denote the so called *default gateway* in TCP/IP networking ...) can be used to have the web site's URL point to an impossible-to-reach address. Example:

```
192.168.1.1	yourhostnamehere	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	yourhostnamehere	localhost6.localdomain6	localhost6
127.0.1.1	yourhostnamehere

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 

#
# List of undesired web sites
#

0.0.0.0  www.some-undesired-web-site.com
0.0.0.0  www.some-other-undesired-web-site.com
0.0.0.0  www.russian-spam-site.ru
0.0.0.0  www.swedish-piracy-site.se
0.0.0.0  www.swiss-one-click-hoster.ch
0.0.0.0  www.another-undesired-site.de

```

Now when you try to access those web sites your browser will throw an error, the website will appear to be unreachable.

For this to work properly the file **/etc/nsswitch.conf** should look like this (and it usually does by default):

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

**hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4**
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

What happens here is that your **/etc/hosts** file will override any value any DNS server returns, hence blocking your Ubuntu system from correctly resolving any undesired web site.

To undo those changes you simply add a comment sign "#" in front of the line. Whatever is written after that sign will be ignored (see my example above).

---

### Post by decoherence on 2011-08-16
The /etc/hosts solution will block entire domains, which isn't necessarily the same thing as blocking specific web sites.

Perhaps the poster should check out Dan's Guardian if /etc/hosts isn't appropriate. I haven't used it myself but I understand this is what it's used for.

---

### Post by scorp123 on 2011-08-17
> **decoherence said:**
> The /etc/hosts solution will block entire domains  How so? As the name suggests it is used for resolving single **hosts** ... hence the name.

The manual is your friend:
```
man hosts
```

... will give you the manual:
```

HOSTS(5)                                                                  Linux Programmer's Manual                                                                  HOSTS(5)

NAME
       hosts - The static table lookup for **hostnames**

SYNOPSIS
       /etc/hosts

DESCRIPTION
       This  manual  page describes the format of the /etc/hosts file.  **This file is a simple text file that associates IP addresses with hostnames, one line per IP address.**
       For each host a single line should be present with the following information:

              IP_address canonical_hostname [aliases...]

       Fields of the entry are separated by any number of blanks and/or tab characters.  Text from a "#" character until the end of the line is a comment,  and  is  ignored.
       Host  names may contain only alphanumeric characters, minus signs ("-"), and periods (".").  They must begin with an alphabetic character and end with an alphanumeric
       character.  Optional aliases provide for name changes, alternate spellings, shorter hostnames, or generic hostnames (for example, localhost).

       The Berkeley Internet Name Domain (BIND) Server implements the Internet name server for Unix systems.  It augments or replaces the /etc/hosts file or hostname lookup,
       and frees a host from relying on /etc/hosts being up to date and complete.

       In modern systems, even though the host table has been superseded by DNS, it is still widely used for:

       bootstrapping
              Most systems have a small host table containing the name and address information for important hosts on the local network.  This is useful when DNS is not run&#8208;
              ning, for example during system bootup.

       NIS    Sites that use NIS use the host table as input to the NIS host database.  Even though NIS can be used with DNS, most NIS sites still use the host table with an
              entry for all local hosts as a backup.

       isolated nodes
              Very  small  sites  that are isolated from the network use the host table instead of DNS.  If the local information rarely changes, and the network is not con&#8208;
              nected to the Internet, DNS offers little advantage.

....
```

---

