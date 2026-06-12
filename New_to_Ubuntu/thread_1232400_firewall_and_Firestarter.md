---
title: "firewall and Firestarter"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by pgte3 on 2009-08-05
I few questions about firewalls in ubuntu 9.04:

After a fresh install of ubuntu 9.04 is there a firewall running?

What does it appear as in the top command output?

After installing Firestarter and rebooting is there a firewall running, what does it appear as in the top command output?

Now starting Firestarter what does it and the firewall appear as in the top command output?

Thanks, pgte3

---

### Post by oldos2er on 2009-08-05
Firestarter's not a firewall, it's a somewhat dated firewall configuration program for iptables. May I suggest you read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mcduck on 2009-08-05
> **pgte3 said:**
> I few questions about firewalls in ubuntu 9.04:

After a fresh install of ubuntu 9.04 is there a firewall running?

What does it appear as in the top command output?

After installing Firestarter and rebooting is there a firewall running, what does it appear as in the top command output?

Now starting Firestarter what does it and the firewall appear as in the top command output?

Thanks, pgte3

No, there isn't a firewall running by default. Default install of Ubuntu doesn't have any running services that would respond to incoming connections from network so a firewall isn't needed. Of course if you install any server software you'll want to get a firewall as well.

After installing Firestarter it will run automatically on boot. The actual firestarter script, that is, the GUI tool is just for configuring the firewall and doesn't need to be running. To check Firestarter's status you can use following command:

```
sudo /etc/init.d/firestarter status
```

Of course it should be mentioned that Firestarter isn't the actual firewall, at least not in the same sense as Windows firewall programs are. All the actual tools and components used to control the network traffic are built into Linux itself (netfilter/iptables), you just need some way to load the firewall rules at boot, and that's what Linux firewalls are. Scripts that set your firewall rules. Firestarter just adds a GUI tool for configuring it's script..

By the way, I recommend using UFW (or Gufw, if you want a graphical tool) instead of Firestarter. It works better with Ubuntu and is more actively developed..

---

### Post by pgte3 on 2009-08-05
Thanks for the posts.

Yes I agree the Firestarter is not the firewall.

After installing Firestarter and rebooting is there a firewall running, what does it appear as in the top (or some other command) command output?

Thanks, pgte3

---

### Post by philinux on 2009-08-05
Have a read through this.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by mcduck on 2009-08-05
> **pgte3 said:**
> Thanks for the posts.

Yes I agree the Firestarter is not the firewall.

After installing Firestarter and rebooting is there a firewall running, what does it appear as in the top (or some other command) command output?

Thanks, pgte3

Actually I already answered that as well.. After installing Firestarter it will run on every boot and load the firewall rules for you.

I can't check what name it uses in top, I haven't used Firestarter for years. But the command I gave you will tell you if Firestarter is running or not.

You can of course always also check your iptables rules with this command:
```
sudo iptables -L
```

---

### Post by pgte3 on 2009-08-05
Thanks for the post. If Firestarter is not the firewall, just a way to work with rules and load rules, what about installing Firestarter starts the firewall? How do I see the firewall running, or is it just part of the kernel so I will not see it running?

For example I bring up Firestarter GUI and make one simple rule to block one ip address, and "apply" that rule. I then shutdown the Firestarter GUI. I should not see Firestarter running correct? What will be running and enforcing the rule?

Thanks, pgte3

---

### Post by XCan on 2009-08-05
mcduck gave you the answer. You can check which rules are on by typing his command.

---

### Post by mcduck on 2009-08-05
Firestarter has two parts, Firestarter script which runs as system service and loads the firewall rules to iptables, and then the GUI which is used to edit the Firestarter script.

So, in the boot, the Firestarter script is started and it starts your firewall. Any changes you make in the GUI will simply change the rules in the script.

So, if you use the command I've given you (twice) you should see the script being running. It will also show in top and other process listings, but like I said I'm not using Firestarter so I can't check what name the script has.

The GUI is completely separate process from the firewall script itself. So when you have the GUI open you have two processes, the GUI and the script. When you close the GUI you only have the script running.

---

### Post by pgte3 on 2009-08-05
Thanks mcduck.

You have shown me how to see the script running, which is the firewall rules.

You said "So, in the boot, the Firestarter script is started and it starts your firewall"

How do I see the firewall running?

---

### Post by mcduck on 2009-08-05
```
sudo iptables -L
```
This will list the rules iptables is using at the time. By default there are only couple of rules that accept any traffic, with firewall active you'll see all your filtering rules there.

That's as much as you are going to get. There's no flashy lights or pretty tools to tell you that the firewall is running. If iptables lists you firewall rules then you have a working firewall.

---

### Post by pgte3 on 2009-08-05
Thanks mcduck for your patience, you have been helpful.

---

