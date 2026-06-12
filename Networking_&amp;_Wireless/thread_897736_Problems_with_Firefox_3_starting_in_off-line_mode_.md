---
title: "Problems with Firefox 3 starting in off-line mode under Hardy"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2008-08-22
Apparently there is some bug in either Firefox 3 and/or Ubuntu/Hardy that makes the browser unable to browser the internet because it comes up in some type of offline mode.

My question is will this same problem be present if I uninstall Firefox 3 and install Opera as the browser instead ?

I know that I could just try it and see but I would rather not compound these problems if someone already knows the answer to this question.

Thanks.

---

### Post by okey666 on 2008-08-22
If it says it is in off line mode, go file>>work offline and refresh.

If this does not work then opera will probably fix it.

---

### Post by simpleone on 2008-08-22
Here author have a same problem with Firefox, Evolution and Liferea, find and post solution:
[http://ubuntueasy.com/internet/boremsja-s-modnymi-obnovlenijami](http://ubuntueasy.com/internet/boremsja-s-modnymi-obnovlenijami)

What to do:

sudo mcedit /etc/dbus-1/system.d/NetworkManager.conf

you can see something like this:

<!DOCTYPE busconfig PUBLIC
"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="root">
<allow own="org.freedesktop.NetworkManager"/>

<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy user="haldaemon">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy at_console="true">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy context="default">
<deny own="org.freedesktop.NetworkManager"/>
<deny send_destination="org.freedesktop.NetworkManager"/>
<deny send_interface="org.freedesktop.NetworkManager"/>
</policy>

<limit name="max_replies_per_connection">512</limit>
</busconfig>

replace it with:

<!DOCTYPE busconfig PUBLIC
"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="root">
<allow own="org.freedesktop.NetworkManager"/>

<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy user="haldaemon">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy at_console="true">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy context="default">
<deny own="org.freedesktop.NetworkManager"/>
<deny send_destination="org.freedesktop.NetworkManager"/>
<deny send_interface="org.freedesktop.NetworkManager"/>
</policy>

<limit name="max_replies_per_connection">512</limit>
</busconfig>

And all work!

---

### Post by wpshooter on 2008-08-22
> **simpleone said:**
> Here author have a same problem with Firefox, Evolution and Liferea, find and post solution:
[http://ubuntueasy.com/internet/boremsja-s-modnymi-obnovlenijami](http://ubuntueasy.com/internet/boremsja-s-modnymi-obnovlenijami)

What to do:

sudo mcedit /etc/dbus-1/system.d/NetworkManager.conf

you can see something like this:

<!DOCTYPE busconfig PUBLIC
"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="root">
<allow own="org.freedesktop.NetworkManager"/>

<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy user="haldaemon">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy at_console="true">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**allow send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy context="default">
<deny own="org.freedesktop.NetworkManager"/>
<deny send_destination="org.freedesktop.NetworkManager"/>
<deny send_interface="org.freedesktop.NetworkManager"/>
</policy>

<limit name="max_replies_per_connection">512</limit>
</busconfig>

replace it with:

<!DOCTYPE busconfig PUBLIC
"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
<policy user="root">
<allow own="org.freedesktop.NetworkManager"/>

<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy user="haldaemon">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy at_console="true">
<allow send_destination="org.freedesktop.NetworkManager"/>
<**deny send_interface**="org.freedesktop.NetworkManager"/>
</policy>
<policy context="default">
<deny own="org.freedesktop.NetworkManager"/>
<deny send_destination="org.freedesktop.NetworkManager"/>
<deny send_interface="org.freedesktop.NetworkManager"/>
</policy>

<limit name="max_replies_per_connection">512</limit>
</busconfig>

And all work!

IF this is the solution to this internet browsing problem, how come this has not been fixed and made available in the update manager fuction of Ubuntu ?

Thanks.

---

### Post by 2beers on 2008-09-12
I found a different sollution.
The one mentioned above works, yet i don't wanna switch of that function in my network manager, as it seems, it has to be solvable in FF as well.
And it is:
(info from: [http://forum.ubuntuusers.de/topic/firefox-3-startet-im-offline-modus/2/?highlight=firefox+offlin+modus](http://forum.ubuntuusers.de/topic/firefox-3-startet-im-offline-modus/2/?highlight=firefox+offlin+modus) (de))
1.) in about:config set browser.offline to false (was allready in my case).

2.) in about:config set toolkit.networkmanager.disable to true.
Regards

---

