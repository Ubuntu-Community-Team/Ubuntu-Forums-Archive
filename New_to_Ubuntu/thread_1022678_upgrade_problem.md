---
title: "upgrade problem"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-12-27
i'm having problem to upgrade my ubuntu8.04 hardy heron which i've recently installed.
an error msg is issued : **Not all updates can be installed**
and it asked me to run partial upgrade. in doing so, another error msg is issued : [B]could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.
[/B]
what should i do? wait and try agian later? for how long to wait? is there a way to counter it?

---

### Post by RajaAjmal on 2008-12-27
sorry. in fact it's update problem and not upgrade.

---

### Post by billgoldberg on 2008-12-27
Open up a terminal and do

```
sudo apt-get update
```

What errors does it give?

--

Open a terminal and past this command, then post the contents of the file here:

```
gksudo gedit /etc/apt/sources.list 
```

--

Also you could try another mirror.

You can use synaptic for that *(can't remember how to do it off the top of my mind, I'm on Arch linux)*.

Google: "ubuntu change repository mirror".

---

### Post by zvacet on 2008-12-27
To change mirror **system>admin>software sources**

---

