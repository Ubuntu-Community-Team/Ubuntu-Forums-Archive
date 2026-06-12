---
title: "network-manager-pptp in Intrepid 8.10"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by tritium3 on 2008-11-26
[FONT="Courier New"]For those of you who can answer "yes" to all five of the following questions:

* Are you using Intrepid?
* Do you neither use nor require the new features of NetworkManager 0.7 such as "Mobile Broadband" and "DSL"?
* Are you having troubles with network-manager-pptp in Intrepid?
* Do you want to stay with Intrepid?
* Do you want to revert Intrepid's network-manager-pptp to be as it was in Hardy?
* Are you willing to take risks and not blame me if something goes wrong?

I've created "new" versions of the five related packages with version numbers such that they are "newer" than 0.7, but are actually the same packages and versions which were in Hardy. These are only for the i386 architecture. I've tested them as well as I can and would like volunteers for additional testing. I did not sign these packages, so you will have to understand what that means. To become a volunteer tester, do these steps:

1. Add the following to Software Sources:
deb http://www2.nau.edu/wal2/NetworkManager/ ./

2. Use update-manager or synaptic to check the software channels for new updates or reload the package information.

3. For your information, the "new" versions of the five packages are:
libnm-glib0            0.7+0.6.6
libnm-util0            0.7+0.6.6
network-manager        0.7+0.6.6
network-manager-gnome  0.7+0.6.6
network-manager-pptp   0.7+0.6.5

4. Install all five of the packages shown in #3 above, after verifying that the "new" version is as listed in #3 above.

5. Reboot, just be safe

6. If you previously used network-manager-pptp under Hardy, it should look exactly like it did in Hardy. If you had not previously used network-manager-pptp under Hardy, take a look at the configuration dialogs.

7. Set up your favorite pptp connection and test it.[/FONT]

---

### Post by whoop on 2008-11-26
ouch! I think that's a really nasty way of "fixing" the problems in network-manager-pptp. I cannot even begin to think what kind of problems one can get themselves into like that.

---

### Post by tritium3 on 2008-11-29
I've created a document explaining how to do it AND undo it, as well as the history behind it all, here:

[http://www2.nau.edu/wal2/NetworkManager/Readme.html]("http://www2.nau.edu/wal2/NetworkManager/Readme.html")

---

