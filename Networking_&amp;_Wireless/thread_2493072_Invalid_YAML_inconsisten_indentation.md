---
title: "Invalid YAML: inconsisten indentation"
date: 2023-12-02
forum: Networking &amp; Wireless
---

### Post by kotgc on 2023-12-02
Hello,
I've only used spaces, no tabs and the indentation looks correct.
I even screencast the typing of the new file and all I do is backspace twice?
Can't attach the screencast.webm 830.3 kB file.

```
ubuntu@ubuntu:/etc/netplan$ ls
01-netcfg.yaml  01-netcfg.yaml.202312022204  01-netcfg.yaml.origin  01-network-manager-all.yaml
ubuntu@ubuntu:/etc/netplan$ cat 01-netcfg.yaml
network:
  network:
    version: 2
    renderer: networkd
    ethernets:
      enp2s0:
        dhcp4: false
        dhcp6: false
        link-local []
      enp3s0:
        dhcp4: false
        dhcp6: false
        link-local []
      bridges:
        br0:
          interfaces: [enp3s0]
          dhcp4: false
          dhcp6: false
          link-local []
          macaddress: a8:a1:59:6e:1f:8b
          parameters:
            stp: false
        br1:
          interfaces: [enp2s0]
          dhcp4: false
          dhcp6: false
          link-local []
          addresses: [192.168.1.120/24]
          macaddress: 1c:61:b4:6d:38:4f
          routes:
            - to: default 
              via: 192.168.1.170
            nameservers:
              addresses: [8.8.8.8]
            parameters:
              stp: false
ubuntu@ubuntu:/etc/netplan$ sudo netplan apply
[sudo] password for ubuntu: 
/etc/netplan/01-netcfg.yaml:10:7: Invalid YAML: inconsistent indentation:
      enp3s0:
      ^

```

---

### Post by TheFu on 2023-12-02
Delete the 2nd 

```
  network:
```

line. Also, the 
```
      bridges:
```
line and everything inside it is on the wrong level. Needs to be on the same level as "ethernets".

---

### Post by The Cog on 2023-12-02
I also think that all the lines "**[FONT=Courier New]link-local [][/FONT]**" should have a colon: "**[FONT=Courier New]link-local: [][/FONT]**"

---

### Post by TheFu on 2023-12-02
> **The Cog said:**
> I also think that all the lines "**[FONT=Courier New]link-local [][/FONT]**" should have a colon: "**[FONT=Courier New]link-local: [][/FONT]**"

Or just remove them.  Are they required now?  None of my netplan files has any mention of local-link.

---

### Post by bobunderwood99 on 2023-12-02
Try using a YAML validator - like at

[https://appdevtools.com/yaml-validator](https://appdevtools.com/yaml-validator) 

or

[https://yamlchecker.com/](https://yamlchecker.com/)

---

### Post by kotgc on 2023-12-02
Thanks for the feedback.
I'll try removing the link-local: [] lines after the other errors are cleared, as the file works on SSD1 (/dev/sda), but I'm testing installing on SSD2 (/dev/sdb).
The YAML validators say the code is good after editing your suggestions.
However on my machine, the error appears:
```

ubuntu@ubuntu:/etc/netplan$ ls
01-netcfg.yaml  01-netcfg.yaml.202312022204  01-netcfg.yaml.origin  01-network-manager-all.yaml
ubuntu@ubuntu:/etc/netplan$ cat 01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: false
      dhcp6: false
      link-local: []
    enp3s0:
      dhcp4: false
      dhcp6: false
      link-local: []
    bridges:
      br0:
        interfaces: [enp3s0]
        dhcp4: false
        dhcp6: false
        link-local: []
        macaddress: a8:a1:59:6e:1f:8b
        parameters:
          stp: false
      br1:
        interfaces: [enp2s0]
        dhcp4: false
        dhcp6: false
        link-local: []
        addresses: [192.168.1.120/24]
        macaddress: 1c:61:b4:6d:38:4f
        routes:
          - to: default 
            via: 192.168.1.170
        nameservers:
          addresses: [8.8.8.8]
        parameters:
          stp: false
ubuntu@ubuntu:/etc/netplan$ sudo netplan apply
/etc/netplan/01-netcfg.yaml:14:7: Error in network definition: unknown key 'br0'
      br0:
      ^

```

---

### Post by ian-weisser on 2023-12-02
bridges: and everything it contains should be reduced two spaces. @TheFu told you this in Post #2.

bridges: is not subordinate to ethernets:

---

### Post by aljames2 on 2023-12-02
> **ian-weisser said:**
> bridges: and everything it contains should be reduced two spaces.

bridges: is not subordinate to ethernets:

Yep, that was my problem exactly recently with a YAML file involving a bridge.  Spacing & alignment are not meaningless.

---

### Post by The Cog on 2023-12-02
As TheFu pointed out in #2, the line containing word bridges and every line afterwards need their indent reducing by 2 spaces. At the moment, "bridges" looks like the name of a third ethernet, which it isn't. Also, routes, nameservers and parameters need outdenting (2 levels, I think) because at the moment they look like properties of br1.

I find a 4-space indent is clearer to read than 2-spaces. This might be right for you. Not sure, but at least it's valid yaml:
```
network:
    version: 2
    renderer: networkd
    ethernets:
        enp2s0:
            dhcp4: false
            dhcp6: false
            link-local: []
        enp3s0:
            dhcp4: false
            dhcp6: false
            link-local: []
    bridges:
        br0:
            interfaces: [enp3s0]
            dhcp4: false
            dhcp6: false
            link-local: []
            macaddress: a8:a1:59:6e:1f:8b
            parameters:
                stp: false
        br1:
            interfaces: [enp2s0]
            dhcp4: false
            dhcp6: false
            link-local: []
            addresses: [192.168.1.120/24]
            macaddress: 1c:61:b4:6d:38:4f
    routes:
        - to: default
          via: 192.168.1.170
    nameservers:
        addresses: [8.8.8.8]
    parameters:
        stp: false
```

---

### Post by kotgc on 2023-12-02
Thanks, all fixed. I like the 4 space indent to fool proof these errors OR perhaps the 2 YAML code checker websites might do it.

---

### Post by TheFu on 2023-12-03
> **kotgc said:**
> Thanks, all fixed. I like the 4 space indent to fool proof these errors OR perhaps the 2 YAML code checker websites might do it.

It is easily possible to have invalid YAML for a specific config, yet pass YAML validators.  YAML is better for humans than json and xml, but not as good as the old inifile format that humans have been trained to understand.  Sigh.

Wish there were a format that was both good for computers to parse AND good for humans.   I have an idea, perhaps like the format in the /etc/network/interfaces file?  Crazy idea, but we used that for many decades and having 1 extra space didn't break everything.  Distros that push YAML should rethink their audience needs.

---

### Post by The Cog on 2023-12-03
Glad that's OK.
There is a program called yamllint in the repositories. Just say "[FONT=Courier New]**yamllint <filename>**[/FONT]" and it will pour criticism on your creation. In theory a yaml document should begin with a line of three dashes, but most people don't bother. It bitches about that though.

Of course, it's possible to have valid YAML that doesn't make sense in context, such as where **bridges** was another ethernet interface or **routes** was a property of bridge **br1**.

@TheFu: I don't think INI files were able to do nested structures though. I suppose dotting everything might be an option, like:
```
network.ethernets.enp2s0.dhcp4 : false
network.ethernets.enp2s0.dhcp6 : false
network.ethernets.enp2s0.link-local : []
network.ethernets.enp3s0.dhcp4 : false
network.ethernets.enp3s0.dhcp6 : false
network.ethernets.enp3s0.link-local : []
network.bridges.br0.interfaces: [enp3s0]
```
but to be honest, I prefer YAML to that.

I have to say, I don't understand the structure that I posted above - it seems that both Ethernet interfaces are also bridge interfaces and that doesn't make sense to me. Maybe it means the ethernet interfaces are connected to the bridges? One day I'll look that up, but right now breakfast is more urgent.

---

### Post by TheFu on 2023-12-03
> **The Cog said:**
>   ... 
I have to say, I don't understand the structure that I posted above - it seems that both Ethernet interfaces are also bridge interfaces and that doesn't make sense to me. Maybe it means the ethernet interfaces are connected to the bridges? One day I'll look that up, but right now breakfast is more urgent.

Before XML existed, I wrote code to support import/export of non-trivial data structures with 5-levels of nesting for a commercial product. It was custom, but used iniFile as the basis.  Nested objects were allowed in any order, since the code would parse it all and layout the relationships before creating all the DB objects.  Our clients and support people had no problems understanding the required parent-child relationships.  Within the file to be imported, the connections between parent and child object had to be consistent, but wasn't used literally inside the system to make connections.  We used orefs for that.  Object-References are like a "Class::Sequence" way of looking at individual computer objects.  Every object of the same class would begin with the same 6 characters.  System objects would have sequences less than 10,000 and end-user objects had sequences that started at 10,001 but effectively had no limit ... (4 billion?)  Running out was never considered possible and we never saw it happen.

Anyway, it wasn't exactly thrilling code.  Think of detailed parts books and being able to setup a DBMS schema to allow importing millions of different part types, many similar, but many completely different.  The attributes for those parts are provided in books that look like the old phone books on very thin paper.  Average people come across these perhaps at the autostore when they look up the replacement air and oil filter for their cars.  Those are just 2 parts. Imagine you are a business and sell "things" using over a million different parts.  Your engineering teams need to know what parts are available, from whom, and what all the attributes are for each part.  How many sizes and types of screws are there in the world?  

I can't imagine how hard it would have been to force the non-technical clients to learn the intricacies of YAML whitespace requirements.  Whitespace requirements seem like a good idea until you see someone non-technical trying to figure it out themselves.  I've written parsers that needed to handle any input a human might decide to throw at it.  Machine to machine communications is like an airliner autopilot, but when humans get involved, it is more like self-driving vehicles in a constantly changing city.  autopilots are relatively simple compared to self-driving on city streets with humans trying to screw with the algorithm of the machine.  Pilots are trained to only provide very, specific, approved, inputs to their plane.  Humans outside flying planes control spacing to ensure slight location mistakes don't cause crashes.  The more dense the planes are in an area, the more tightly controlled where, when, how fast, they are allowed to fly.  If only YAML were like that.

Let machines have their method for configs and let humans have their own.   Machines can export/import xml/json/yaml no problem.  Of those 3, yaml is the easiest for humans to modify.  I have some web servers that will output html, xml, json, or yaml, based on what is requested by the client.  It is handy for RESTful client/server needs for APIs that are automatically available.  We have **sfdisk** for machines to dump their partitions to machine-readable text.  We have fdisk for humans.

Anyway, there are lots of precedents already.

A shower is more urgent to me, and everyone around here, than b'fast. ;)

---

### Post by kotgc on 2023-12-03
Replying to post #4 TheFu, yes, the link-local: [] line can be deleted. I tested and works fine.

---

