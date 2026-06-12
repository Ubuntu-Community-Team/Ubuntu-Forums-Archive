---
title: "Cannot find a way to add a static IP address to bond"
date: 2022-04-15
forum: Networking &amp; Wireless
---

### Post by jbruyet on 2022-04-15
I just downloaded and installed 20.04.4 LTS and in the installation process I bonded two NICs. Now that the server is up and running (on one of the two other NICs) I can't find a way to apply a static address to the bond. I've Googled this but none of the results I've looked at look like my .yaml (I'm more familiar with Debian, but my software vendor...) file and thus far none of the CLI commands work either. I have, in the past, done some manual settings in the file but when I open this file there's a message across the top of the screen: "# This is the network config written by 'subiquity.'" Googling that error message hasn't helped either. Any ideas, suggestions, or recommendations? 

Thanks,

Joe B

---

### Post by chili555 on 2022-04-16
> there's a message across the top of the screen: "# This is the network config written by 'subiquity.'" Googling that error message hasn't helped either. That's not an error message, it is informational. What does the remainder of the file say?

Have you checked here? [https://netplan.io/examples/](https://netplan.io/examples/)

---

### Post by jbruyet on 2022-04-18
Good morning chili555, 

I looked there but I wasn't able to find information on the correct syntax or spacing. Rather than do the "experiment and hope for the best" thing I was hoping for some guidance on the physical editing of the file. I have read that horizontal line spacing has to be just right, but I have yet to find an online example like mine: 

# This is the network config written by 'subiquity'
```
network:
  bonds:
    bond0:
      interfaces:
      - eno1
      - eno2
      parameters:
        mode: balance-rr 
  ethernets:
    eno1: {}
    eno2: {}
    eno3:
      dhcp4: true
    eno4:
      dhcp4: true
  version: 2
00-installer-config.yaml
```

Where would I start entering the static address information and what would be the correct line indentation? Oh, and some version information: 

```
jbruyet@veeamsec:/etc$ cat os-release
NAME="Ubuntu"
VERSION="20.04.4 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.4 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
jbruyet@veeamsec:/etc$
```




Thanks, 

Joe B

---

### Post by chili555 on 2022-04-18
There are examples right on your system in /usr/share/doc/netplan/examples/.

For instance:

```
cat /usr/share/doc/netplan/examples/bonding.yaml
```

```
network:
  version: 2
  renderer: networkd
  bonds:
    bond0:
      dhcp4: yes
      interfaces:
        - enp3s0
        - enp4s0
      parameters:
        mode: active-backup
        primary: enp3s0

```After you edit the file, follow with:

```
sudo netplan generate
sudo netplan apply
```

I'd adapt the static example to your situation:

```
cat /usr/share/doc/netplan/examples/static.yaml
```

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 10.10.10.2/24
      nameservers:
        search: [mydomain, otherdomain]
        addresses: [10.10.10.1, 1.1.1.1]
      routes: 
        - to: default
          via: 10.10.10.1

```In other words, remove the dhcp lines and add the address, nameserver and routes, properly indented of course.

I know litlle (well, nothing, really) about bonding, except bonding saved me from a day in jail, once. However, I know where the examples are kept.

---

### Post by jbruyet on 2022-04-18
I redid my .yaml file, but now I'm getting this error message on generate: 

```
/etc/netplan/00-installer-config.yaml:26:1: Invalid YAML: aliases are not supported:
```


And here is my current copy of my .yaml file: 

# This is the network config written by 'subiquity'
```
network:
  bonds:
    bond0:
      address: 192.168.2.30
      netmask: 255.255.255.0
      gateway: 192.168.2.1
      nameservers: 
        addresses: 192.168.2.89, 192.168.1.39
        search: link.com


      interfaces:
      - eno1
      - eno2
      parameters:
        mode: balance-rr 
  ethernets:
    eno1: {}
    eno2: {}
    eno3:
      dhcp4: true
    eno4:
      dhcp4: true
  version: 2
00-installer-config.yaml
``` (END)


There aren't any carriage returns after the (END) line. 

I did have an earlier error that said to not use tabs, but opening the file in vim helped me to find and fix those errors. I guess Notepad++ doesn't accurately translate to Linux-speak... 

Thanks, 

Joe B

---

### Post by jbruyet on 2022-04-18
Um, there really are indentations in my file. I don't know why they didn't show up here...

Thanks, 

Joe B

---

### Post by jbruyet on 2022-04-18
Here's another try with my file...

```
jbruyet@veeamsec:/etc/netplan$ cat 00-installer-config.yaml# This is the network config written by 'subiquity'
network:
  bonds:
    bond0:
      address: 192.168.2.30
      netmask: 255.255.255.0
      gateway: 192.168.2.1
      nameservers:
        addresses: 192.168.2.89, 192.168.1.39
        search: link.com


      interfaces:
      - eno1
      - eno2
      parameters:
        mode: balance-rr
  ethernets:
    eno1: {}
    eno2: {}
    eno3:
      dhcp4: true
    eno4:
      dhcp4: true
  version: 2
00-installer-config.yaml (END)
jbruyet@veeamsec:/etc/netplan$



```

---

### Post by chili555 on 2022-04-18
> <snip>
dhcp4: true
eno4:
dhcp4: true
version: 2
[COLOR="#FF0000"]00-installer-config.yaml (END)[/COLOR]Is the highlighted text really in the file? If so, please remove it and try again.

---

### Post by jbruyet on 2022-04-18
Nope, I'm still getting the "aliases are not supported:" error. 

Bummer, 

Joe B

---

### Post by chili555 on 2022-04-18
```
bond0:
      address: 192.168.2.30
      netmask: 255.255.255.0
      gateway: 192.168.2.1
      nameservers:
        addresses: 192.168.2.89, 192.168.1.39
        search: link.com
```
        
        
I suggest that this should be:

```
bond0:
  addresses:
    - 192.168.2.30/24
  nameservers:
    addresses: [192.168.2.89, 192.168.1.39]
    search: link.com 
  routes: 
    - to: default
      via: 192.168.2.1 
```

---

### Post by jbruyet on 2022-04-18
Here's what I'm now seeing:

```
jbruyet@veeamsec:/etc/netplan$ sudo netplan generate/etc/netplan/00-installer-config.yaml:7:7: Invalid YAML: did not find expected '-' indicator:
      nameservers:
      ^
jbruyet@veeamsec:/etc/netplan$



```

---

### Post by chili555 on 2022-04-18
```
 nameservers:
 ^
```I think that means that the identation is off. Please check and correct.

---

### Post by jbruyet on 2022-04-18
Ok, I have no more indentation errors. Yay! 

However, I now have the following error:
```

jbruyet@veeamsec:/etc/netplan$ sudo netplan generate
/etc/netplan/00-installer-config.yaml:23:1: Invalid YAML: aliases are not supported:


^
jbruyet@veeamsec:/etc/netplan$

```

I have no idea what it's pointing to. Thanks Chili555 for the help. I should have been gone by now so I'm outta here. I will look for any other suggestions when I get here tomorrow. 

Thanks,

Joe B

---

### Post by jbruyet on 2022-04-18
I just took another quick look (yeah, I know it's late...) and the error line shows "23:1." is that line 23 character 1? If so my problem may be deeper than I thought - my yaml file only has 22 lines in it. 

Really, truly outta here. 

Joe

---

### Post by The Cog on 2022-04-19
I put the content of post #7 into a file called ZZZ.yml and ran yamllint on it:
```
$ yamllint ZZZ.yml 
ZZZ.yml
  1:1       warning  missing document start "---"  (document-start)
  13:7      error    wrong indentation: expected 8 but found 6  (indentation)
  26:1      error    syntax error: could not find expected ':'
```
You can ignore the warning about start of document missing. That's not actually necessary in this context.
Line 13 seems like a valid complaint.
Line 26 is due to line 25 starting "00" - which looks a bit like the first part of an unfinished yaml declaration - delete this line.

yamllint is not checking the meaning of the config file - just that it is valid yaml.

---

### Post by jbruyet on 2022-04-19
Thanks The Cog, 

I tweaked the file and was rewarded with a nice green "Valid YAML!" message. BUT, I put that yaml back in the server, did a sudo netplan generate, and now I'm getting a different error: 

```
jbruyet@veeamsec:/etc/netplan$ sudo netplan generate/etc/netplan/00-installer-config.yaml:8:11: Error in network definition: bond0: interface 'eno2' is not defined
        - eno2
          ^
jbruyet@veeamsec:/etc/netplan$
```

I think I'm going to do a "Nuke and Repopulate" on this server. The installation went smoothly, and everything has worked up until this point, but I'm now seeing yaml files when I close my eyes. 

Also, that YAMLlint site is great!

Thanks, 

Joe B

---

### Post by The Cog on 2022-04-19
> Also, that YAMLlint site is great!
I had no idea that site existed. I don't think I like it - it seems to auto-correct invalid yaml. I'm not convinced it would always autocorrect it in the "right" way - retaining the "meaning" I want.

The yamllint I used was the yamllint package for Ubuntu, which criticises invalid yaml without altering the file:
```
sudo apt install yamllint
yamllint myfile.yml
```

---

### Post by jbruyet on 2022-04-19
Thanks Cog. I haven't worked with Ubuntu for a very long time, thusly the yaml files do not compute. I had done a quick search for the yamllint program but never found. Once I get this server up and running I will install it. 

In my first install I had Ubuntu whip up a bond connection for me. I think I'll just do NICs this time and do a bond later. 

Thanks for the help and information, 

Joe B

---

### Post by The Cog on 2022-04-20
Incidentally, instead of this notation for a list of interface names:
```
      interfaces:
        - eno1
        - eno2
```
This is equally valid and perhaps easier to understand:
```
      interfaces: [eno1, eno2]
```
These two lines are equivalent and have a different meaning to the above: interfaces is a single string with a space and a comma in the middle of it:
```
      interfaces: eno1, eno2
      interfaces: "eno1, eno2"
```
I would advise always using the brackets or quotes, for the benefit of human users. Yaml is just too permissive for its own good.

---

### Post by jbruyet on 2022-04-20
Thanks Cog, the server is working; kind of. Ok, I commented out the "interfaces" and "mode" lines, put my DNS servers and the search domain in square brackets and now the server is up and I can ping the internet (my default network connectivity test). I can also ping devices on six of the seven subnets here at work, but I can only ping two things on this Ubuntu server's subnet - itself and the router. I checked UFW and the status us inactive. I checked to see if Ubuntu was pingable by devices on two of the other subnets and it is. Is there a default setting that Ubuntu servers by default don't allow same-subnet access??? 

Thanks,

Joe B

---

### Post by The Cog on 2022-04-21
You could check the subnet mask of the troublesome networks. Odd things happen if you get the subnet mask wrong.
The other devices on the network may be firewalled not to let pings in. If you're sure other devices are there, you can try to ping them and then look at "ip neighbor" and see if their MAC address is resolved. If it is, then all is well and the other boxes don't answer pings.

---

### Post by jbruyet on 2022-04-21
There's only one troublesome subnet for this server and that's the subnet it's a part of. I can ping devices on all other subnets and they can ping this server. My computer is on the same subnet as this server and I can ping everything on this subnet. There is a misconfiguration somewhere, but I don't know enough about Ubuntu and YAML to figure it out. 

Thanks, 

Joe B

---

### Post by The Cog on 2022-04-21
OK, let's start with the basics and see if the final configuration is right.
Please post the output of these commands:
```
ip addr
ip route
sudo iptables-save
```
and also, which is the troublesome network/addresses you can't ping?

Another idea occurs to me - you have static IP addresses, yes? Is it possible that you have the same IP address as another machine?

---

### Post by jbruyet on 2022-04-21
Good afternoon The Cog, 

At this time I'm unable to do a cut and paste from the Ubuntu server (and I don't know why). I took pictures of the requested information but they didn't turn out as nice as I had hoped... 

[[IMG]https://i.ibb.co/9WFt7VW/IMG-0408.jpg[/IMG]]("https://ibb.co/vk7YSQk")
[[IMG]https://i.ibb.co/V38gwVh/IMG-0409.jpg[/IMG]]("https://ibb.co/vD83X1r")
[[IMG]https://i.ibb.co/c6qySc1/IMG-0410.jpg[/IMG]]("https://ibb.co/dPZfw0r")
[IMG]https://ibb.co/vk7YSQk[/IMG]

---

### Post by TheFu on 2022-04-21
I dind't read everything, but always, always, always, have an empty line at the end of a file.  Always.  EOL and EOF are not the same for some parsers.  Yes, it shouldn't matter.  No I don't know if it matters here.

Just something I've learned over the decades of Unix administration.

---

### Post by jbruyet on 2022-04-21
Thanks TheFu, I will remember that. 

I did a "Nuke & Repopulate" for my yaml file and I now have all four interfaces bonded and now it's even working locally: 

[SIZE=3][FONT=courier new]2: eno1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    link/ether be:f1:55:19:d6:ca brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]
[SIZE=3][FONT=courier new]3: eno2: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    link/ether be:f1:55:19:d6:ca brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]
[SIZE=3][FONT=courier new]4: eno3: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    link/ether be:f1:55:19:d6:ca brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]
[SIZE=3][FONT=courier new]5: eno4: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    link/ether be:f1:55:19:d6:ca brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]
[SIZE=3][FONT=courier new]6: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    link/ether be:f1:55:19:d6:ca brd ff:ff:ff:ff:ff:ff[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    inet 192.168.2.187/24 brd 192.168.2.255 scope global dynamic bond0[/FONT][/SIZE]
[SIZE=3][FONT=courier new]       valid_lft 690861sec preferred_lft 690861sec[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    inet6 fe80::bcf1:55ff:fe19:d6ca/64 scope link[/FONT][/SIZE]
[SIZE=3][FONT=courier new]       valid_lft forever preferred_lft forever[/FONT][/SIZE]
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$ ping it-2[/FONT][/SIZE]
[SIZE=3][FONT=courier new]PING it-2.link.com (192.168.2.22) 56(84) bytes of data.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]64 bytes from IT-2.link.com (192.168.2.22): icmp_seq=1 ttl=128 time=0.633 ms[/FONT][/SIZE]
[SIZE=3][FONT=courier new]64 bytes from IT-2.link.com (192.168.2.22): icmp_seq=2 ttl=128 time=0.586 ms[/FONT][/SIZE]
[SIZE=3][FONT=courier new]64 bytes from IT-2.link.com (192.168.2.22): icmp_seq=3 ttl=128 time=0.626 ms[/FONT][/SIZE]
[SIZE=3][FONT=courier new]^C[/FONT][/SIZE]
[SIZE=3][FONT=courier new]--- it-2.link.com ping statistics ---[/FONT][/SIZE]
[SIZE=3][FONT=courier new]3 packets transmitted, 3 received, 0% packet loss, time 2011ms[/FONT][/SIZE]
[SIZE=3][FONT=courier new]rtt min/avg/max/mdev = 0.586/0.615/0.633/0.020 ms[/FONT][/SIZE]
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$[/FONT][/SIZE]

If anyone is interested here's my yaml file: 

```
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$ cat 00-installer-config.yaml[/FONT][/SIZE][SIZE=3][FONT=courier new]# This is the network config written by 'subiquity'[/FONT][/SIZE]
[SIZE=3][FONT=courier new]---[/FONT][/SIZE]
[SIZE=3][FONT=courier new]network:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  bonds:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    bond0:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      dhcp4: true[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      interfaces: [eno1, eno2, eno3, eno4][/FONT][/SIZE]
[SIZE=3][FONT=courier new]      parameters:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]        mode: balance-rr[/FONT][/SIZE]
[SIZE=3][FONT=courier new]        #        primary: eno1[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  ethernets:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno1: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno2: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno3: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno4: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  version: 2[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$[/FONT][/SIZE]



```


Yes it's using a DHCP address, but I need to take a quick rest before I try to make it static... 

Thanks all, 

Joe B

---

### Post by jbruyet on 2022-04-22
And here is the completed, functioning YAML file for my four-interface bond: 

```
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$ cat 00-installer-config.yaml
[/FONT][/SIZE][SIZE=3][FONT=courier new]# This is the network config written by 'subiquity'[/FONT][/SIZE]
[SIZE=3][FONT=courier new]---[/FONT][/SIZE]
[SIZE=3][FONT=courier new]network:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  bonds:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    bond0:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      addresses:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]        - 192.168.2.80/24[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      gateway4: 192.168.2.1[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      nameservers:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]        addresses: [192.168.2.89, 192.168.1.39][/FONT][/SIZE]
[SIZE=3][FONT=courier new]        search:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]          - domain.com[/FONT][/SIZE]
[SIZE=3][FONT=courier new]      interfaces: [eno1, eno2, eno3, eno4][/FONT][/SIZE]
[SIZE=3][FONT=courier new]      parameters:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]        mode: balance-rr[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  ethernets:[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno1: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno2: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno3: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    eno4: {}[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  version: 2[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]jbruyet@veeamsec:/etc/netplan$[/FONT][/SIZE]



```
I had some struggles with indentations and hyphens, but now I can ping my local and remote subnet devices using names and addresses. Thanks again to everyone who was helping me out with this. I hope that other people in my situation can find this site and use my config file as a template for configurations for their servers. 

Thanks, 

Joe B

---

