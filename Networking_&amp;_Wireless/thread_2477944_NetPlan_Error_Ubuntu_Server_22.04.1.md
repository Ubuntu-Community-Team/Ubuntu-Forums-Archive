---
title: "NetPlan Error Ubuntu Server 22.04.1"
date: 2022-08-12
forum: Networking &amp; Wireless
---

### Post by coconutdog2 on 2022-08-12
Trying to write a netplan.yaml for my Ubuntu Server 22.04.1 using the following syntax:

```
---
---
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0f0:
      addresses:
      - 10.1.5.62/24
      - 2001:xxxx:xxxx:3b50::62/64
      - fe80::62/64
    enp1s0f1:
      addresses:
      - 10.1.6.62/24
      - 2001:xxxx:xxxx:3b60::62/64
      - fe80::62/64
    enp3s0:
      addresses:
      - 10.1.1.62/24
      - 2001:xxxx:xxxx:3b10::62/64
      - fe80::62/64
#      gateway4: 10.1.1.1
#      gateway6: 2001:xxxx:xxxx:3b10::1
      nameservers:
        addresses:
        - 192.231.203.132
        - 192.231.203.3
        - 2001:xxxx:1::1
        - 2001:xxxx:2::2
      routes:
        - to: default
        - via 10.1.1.1
        - to: default
        - via 2001:xxxx:xxxx:3b10::1
      search:
        - 10.bde.lan
  wifis:
    wlo1:
     optional: true
     access-points:
      "10.secure":
     password: "xxxxxxxxxxxxxxxxxx"
     dhcp4: true
     dhcp6: true
...

```

When validating using netplan --debug apply it stalls at the - via 10.1.1.1 line.
I've run the file through the online yaml verifier ```
https://onlineyamltools.com/validate-yaml
``` which finds no errors.
I'm trying to get rid of the deprecated gateway4 & gateway6 commands. The syntax is accepted using there commands but not the route command.
Does anyone have any ideas?

---

### Post by The Cog on 2022-08-12
1: You have two lines of --- at the top. These are document dividers, so your yaml contains an empty document before the real one. I dont know if this is causing problems, but I would remove one.

2: Most of your list elements are not indented enough. Every list of addresses should be indented to the next level. Some yaml readers will accept the indentation you have used, others will not, So it should look like:
```
    addresses:
      - 1.2.3.4/24
```

3: You are missing a colon after the keyword via (in 2 places) - should read "via:". This is probably your real problem. Missing the colon completely changes the meaning of the line although its still valid yaml syntax.

4: Yamllint (it's in the repos) also complains about the indentation of the comment, but I feel that's personal choice, and it's not an actual error.  
```
  9:7       error    wrong indentation: expected 8 but found 6  (indentation)
  14:7      error    wrong indentation: expected 8 but found 6  (indentation)
  19:7      error    wrong indentation: expected 8 but found 6  (indentation)
  22:1      warning  comment not indented like content  (comments-indentation)
  26:9      error    wrong indentation: expected 10 but found 8  (indentation)
  39:6      error    wrong indentation: expected 6 but found 5  (indentation)
  41:7      error    wrong indentation: expected 7 but found 6  (indentation)
```

---

### Post by coconutdog2 on 2022-08-24
Thanks Mr Cog, I will try your suggestions and see how I go.

---

