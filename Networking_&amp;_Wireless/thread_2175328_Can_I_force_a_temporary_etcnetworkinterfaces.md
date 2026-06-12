---
title: "Can I force a temporary /etc/network/interfaces ?"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by andrew_brown2 on 2013-09-18
[FONT=arial]I would like to be able to validate my /etc/network/interfaces file before saving it permanently. So I wonder if there a way I can restart networking but force networking to load a *different,* [/FONT][FONT=arial]temporarily [/FONT][FONT=arial]interfaces file so that if it fails, rebooting the machine will simply revert back to the original /etc/network/interfaces file which was not modified.

Is this possible? Or can anyone suggest an alternative?

This is for a remote router, so I would really prefer to avoid accidentally taking down all of my interfaces (again.)
[/FONT]

---

### Post by Hadaka on 2013-09-18
Hi, if you boot to the new temp /etc/networkfaces file
and it fails..more than likely your network will come down anyway.
so you could do..
```
sudo cp /etc/network/interfaces /etc/network/old
```
then..
```
sudo gedit /etc/network/interfaces
```
modify the file to the new settings.
boot
*If it fails then do..
```
sudo rm /etc/network/interfaces
sudo mv /etc/network/old /etc/network/interfaces
```
to restore the original old file as was.
boot

---

### Post by andrew_brown2 on 2013-09-19
Thanks.
[INDENT][COLOR=#000000]*If it fails then do..
[/COLOR][/INDENT]

Unfortunately, I can not do this. When the interfaces go down, I would no longer be able to manually restore the config file as you suggest. My question was how to get it to revert on its own automatically after reboot. In other words, my intervention would be required to make it permanent. Without my intervention, the config would revert.

---

### Post by Hadaka on 2013-09-19
ok.. let's say you ssh in and modify your /etc/network/interfaces -temp-
for it to take effect..you have to boot...HOW do you intend to do that?
How will you be booting the remote machine?

---

### Post by ian-weisser on 2013-09-19
You can force a different interfaces file using the ifup -i flag (see man ifup).

The problem is that you need to take the interface(s) down to use it. If you are remote, that will certainly close your connection.
It's not meant for temporary use or validation.

It's not difficult to script a few tests. For example:
```

ifup --interfaces=/etc/network/testinterface1 -a
test_interface a    #Script to test one interface and log the result
test_interface b
ifdown -a
ifup --interfaces=/etc/network/interfaces -a

```

Obviously, you will need to try this on a local machine and smooth out the kinks before even thinking about doing this on a remote machine. There is risk that an interface may not come back up as expected.

---

### Post by andrew_brown2 on 2013-09-21
Ian,

If I am interpreting your code right, you are forcing the use of a different interfaces file but from *within** the standard interfaces file. (*"ifup" is only valid *within* an interfaces file, IIRC.) That defeats my purpose.

I apologize for my difficulty in explaining this very clearly.

The objective is to leave the interfaces file *totally unmodified *so that if something goes wrong, a power cycle will restore the original interface configuration. To apply my test settings, I would want to issue a restart of networking *but with a different interfaces file*. If that config failed, I would power cycle the machine using remote power control. This would force a reboot which would then load back in the original unmodified interfaces file.

If the different interfaces file is loaded *by* the standard interfaces file, it would load it every time, in effect making the changes permanent. I want the temp file loaded only from the command line when I issue a network restart. e.g. something like
```
/etc/init.d/network restart [COLOR=#000000][FONT=Ubuntu Mono]--interfaces=/etc/network/testinterface1[/FONT][/COLOR]
```

---

### Post by andrew_brown2 on 2013-09-21
> **Hadaka said:**
> ok.. let's say you ssh in and modify your /etc/network/interfaces -temp-
for it to take effect..you have to boot...HOW do you intend to do that?
How will you be booting the remote machine?

Good question. I would not apply the temporary interfaces file by a full reboot but by restarting networking somehow applying the temp file only that one time.
But if that config fails, I would perform a full power cycle reboot using remote power control which is independent of the interfaces on this CPU. This I hope to have restore the config to the original save interfaces file.

---

### Post by joeymac2011 on 2013-09-21
FYI:I'm typing this from my ipdod and it's not as convinient for me to elaborate on the detail. 

Here how I would do it. 
1.create a shutdown script that shuts down every 5min. (increase if needed for testing/editing interfaces. Refer adding scrip to include "interfaces" in "/etc/rc.local"
2. Start your testing of the "temp interfaces"

---

### Post by varunendra on 2013-09-21
> **andrew_brown2 said:**
> Good question. I would not apply the temporary interfaces file by a full reboot but by restarting networking somehow applying the temp file only that one time.
But if that config fails, I would perform a full power cycle reboot using remote power control which is independent of the interfaces on this CPU. This I hope to have restore the config to the original save interfaces file.

Can't you do it simply by letting a script do the 'replace - wait - replace again' thing? For example, copy the original file as "interfaces.bak" -
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

Then run a script (as root) that does something like this -
```
#!/bin/bash
# copy the test file from andrew's home
cp -f /home/andrew/interfaces.test /etc/network/interfaces

# restart the networking
service networking restart

# wait for 5 minutes while you can do your tests
sleep 300

# restore the original file from backup
cp -f /etc/network/interfaces.bak /etc/network/interfaces

# restart the networking again
service networking restart
```
You can also add a line "sudo shutdown -r now" in the last if you don't trust that restarting the networking would be able to restore the default connection. But since you have the remote power control over the system, you don't need to worry about that anyway, but make sure you give it enough time to restore the original file back (or add the script to /etc/rc.local to make it run at each boot).

I haven't tested it myself, so you might want to do a test run on a local system before actually trying it.

---

### Post by ian-weisser on 2013-09-21
> **andrew_brown2 said:**
> If I am interpreting your code right, you are forcing the use of a different interfaces file but from *within** the standard interfaces file. (*"ifup" is only valid *within* an interfaces file, IIRC.) That defeats my purpose.


Not quite: Ifup's -i flag forces the use of a *100% different* interfaces file. Not "within" the default (whatever that means). I have used it for the purpose you propose (though under local conditions instead of remote), and it works beautifully.
It does seem to be what you are asking for.


> **andrew_brown2 said:**
> 
The objective is to leave the interfaces file *totally unmodified *so  that if something goes wrong, a power cycle will restore the original  interface configuration. To apply my test settings, I would want to  issue a restart of networking *but with a different interfaces file*.  If that config failed, I would power cycle the machine using remote  power control. This would force a reboot which would then load back in  the original unmodified interfaces file.

If the different interfaces file is loaded *by* the standard  interfaces file, it would load it every time, in effect making the  changes permanent. I want the temp file loaded only from the command  line when I issue a network restart. e.g. something like
```
/etc/init.d/network restart [COLOR=#000000][FONT=Ubuntu Mono]--interfaces=/etc/network/testinterface1[/FONT][/COLOR]
```

Well, power-cycling in case of failure makes it all much easier. Less mucking about testing for failures!
We can do the whole thing in one line, but a rather different line than you propose.

Take a look at the networking sysvinit job (/etc/init.d/networking) and the upstart job (/etc/init/networking.conf).
Neither accept additional arguments with a "restart" command.

Here is a couple ifup/down commands that do essentially the same thing:```

ifdown -a --exclude=lo && ifup -i /etc/network/testinterface1 -a

``` 

No mv, no cp. No permanent change. When you reboot, your original /etc/network/interfaces file gets used again.

Since ifdown will interrupt your connection and clobber your tty...which may prevent the following ifup command prom running, you may wish to trigger the commands from a *screen* instance or cron/at task.

---

