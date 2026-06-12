---
title: "Repository duplicates?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by 5149.5 on 2011-04-05
I am getting nags from apt-get updates lately and I am not sure how I should fix them. Here is an example:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages)

---

### Post by alphacrucis2 on 2011-04-05
> **5149.5 said:**
> I am getting nags from apt-get updates lately and I am not sure how I should fix them. Here is an example:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages)

Edit your /etc/apt/sources.list. You would need root access to update the file so:

```
gksudo gedit /etc/apt/sources.list
```

inspect for duplicates and correct.

---

### Post by 5149.5 on 2011-04-05
> **alphacrucis2 said:**
> Edit your /etc/apt/sources.list. You would need root access to update the file so:

```
gksudo gedit /etc/apt/sources.list
```inspect for duplicates and correct.

I already tried that. Then I noticed that the duplicates occur because of the sources.list file and the /var/lib/apt list file and I wasn't sure which file to modify.

---

### Post by beew on 2011-04-05
Easy way. Open Synaptic, go to Settings > Repositories > Other Software. Find the duplicate and delete the superfulous copy.

---

### Post by calmher on 2011-05-17
> **beew said:**
> Easy way. Open Synaptic, go to Settings > Repositories > Other Software. Find the duplicate and delete the superfulous copy.

Thanks! That definitely worked for me.

---

