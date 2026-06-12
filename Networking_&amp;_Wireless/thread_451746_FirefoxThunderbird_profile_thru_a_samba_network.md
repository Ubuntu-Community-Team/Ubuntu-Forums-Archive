---
title: "Firefox/Thunderbird profile thru a samba network"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by marciovinicius on 2007-05-22
How can I use a profile of Firefox (or Thunderbird) saved in an server using a samba connection?

In Windows, I only have to map the address and point to the paste thru the "profile manager". In Ubuntu the profile manager simply doesn't show network addresses, even if they are already mounted.

---

### Post by marciovinicius on 2007-05-25
Anyone?

---

### Post by deathspal on 2007-08-06
<BUMP> I to would like the answer to this one I use the same profile on my windows and OS-X machines but when I try to brows to the profile location in the profile manager the connected server locations dont show up....  what would the path look like is entered manualy, could I maby even try a link for the path IE( smb://server/share) any help would be great!

---

### Post by tgpfarm on 2007-08-29
i am woking on this though sshfs

---

### Post by marciovinicius on 2007-08-29
> **tgpfarm said:**
> i am woking on this though sshfs
How? What is 'sshfs'?
Sorry, I'm not so experienced in Linux...

---

### Post by ironbark on 2007-10-01
It is possible for the Firefox profile manager to connect to a samba share, **but** you have to either mount the samba share manually from the terminal or put it in fstab. You will need the package **smbfs** to do this.

You mount the share from the terminal with **mount -t smbfs**  command, then you can see it in the left pane of the Firefox profile manager.

Like deathspal said if you can put a firefox profile on a samba share, you will be able to use the same profile across multiple computers and/or operating systems in a networked environment.

---

