---
title: "invalid yaml: inconsistent indentation"
date: 2020-05-30
forum: Networking &amp; Wireless
---

### Post by deheugden on 2020-05-30
Hello,

I am having some issues with networking in Ubuntu LTS Server v20.04
I changed the Yaml into the following:

addresses: [172.16.60.10/8]
gateway4:172.16.11.1
nameservers:
addresses:[172.16.10.10,172.16.10.11]
version 2

but, when applying, sudo netplan apply, i get the following error:

invalid yaml:inconsistent indentation: nameservers:

anyone who knows what i am doing wrong?
also. why doenst the gateway's ip need brackets?

many thanks for any help.

---

### Post by QIII on 2020-05-30
Hello!

If what you have posted is exactly as it appears in your file, then you do have inconsistent indentation.  Indentations in YAML are very specific.

Would you please copy your text *without edits* directly from your file and post it between code tags?

---

### Post by deheugden on 2020-05-30
> **QIII said:**
> Hello!

If what you have posted is exactly as it appears in your file, then you do have inconsistent indentation.  Indentations in YAML are very specific.

Would you please copy your text *without edits* directly from your file and post it between code tags?

many thanks for the fast reply. I am not sure how to copy/paste from VI, so i attached a printscreen.

---

### Post by The Cog on 2020-05-30
See [https://netplan.io/examples](https://netplan.io/examples).
version needs indenting to the same level as ethernets because they are both properties of network.
addresses and nameservers need indenting to the same level to the right of ens33 because they are both properties of ens33.
Beware of mixing spaces and tabs. Use one or the other throughout. Below uses spaces.
```
network:
  ethernets:
    ens33:
      addresses: [172.16.60.10/8]
      gateway4: 172.16.11.1
      nameservers:
        addresses: [172.16.10.10, 172.16.10.11]
  version: 2

```

---

### Post by chili555 on 2020-05-30
> Beware of mixing spaces and tabs.I believe that netplan wants spaces only and not tabs.

---

### Post by The Cog on 2020-05-30
> **chili555 said:**
> I believe that netplan wants spaces only and not tabs.

Ooh yes. You're right. Good for yaml.
I've been caught by python occasionally where files are mixed spaces and tab indentation.

---

