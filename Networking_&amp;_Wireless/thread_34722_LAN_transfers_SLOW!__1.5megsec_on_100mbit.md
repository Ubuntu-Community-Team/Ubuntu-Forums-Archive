---
title: "LAN transfers SLOW!  1.5meg/sec on 100mbit"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by smu johnson on 2005-05-16
Hi there,

I've used Slackware Linux recently, and when I do my famous "scp" test to see the transfer speed between friends on the LAN, I get around 11megs/sec... very nice.

But now that I've installed Ubuntu, I'm seeing extremely sluggish speeds, 1.5megs/sec from my friend.  This didn't happen in Windows either... these slow speeds.  Shut the power off and on on my router, and this didn't help at all...

My NIC is my onboard nForce2 NIC, and it uses forcedeth just like Slackware did... so no difference there.

Any thoughts?  Ubuntu seems SLOW!!!  I did a network test using Iperf, and I don't think it enabled Full Duplex on my NIC because that's when the results go bad.  Anyone have any idea how to check this?  I've looked FOREVER, and everyone keeps saying mii-diag / mii-tool... well this only works for MII bus NICs which I don't have... and there HAS to be another way to find something as simple as the Duplex setting on a NIC (without using dmesg).

Or, if anyone has a solution that fixes the problem, that'd be welcome too :)

Thanks

---

### Post by dataw0lf on 2005-05-16
If your NIC doesn't support mii, you have to pass the duplex setting as a module parameter.  With the nforce cards, this is done like so (I personally don't have one, but I think this is correct):

```
modprobe nvnet force_speed_duplex=4
```

To add this permanently to the module, create a a /etc/modprobe.d/nvnet file and add this to it:
```

options nvnet force_speed_duplex=4
```

These will force your NIC card to 100Mbps Full Duplex.

For more info: 
[http://download.nvidia.com/XFree86/nforce/1.0-0292/ReleaseNotes.html#module_parameters](http://download.nvidia.com/XFree86/nforce/1.0-0292/ReleaseNotes.html#module_parameters)

Addendum: Sorry, just realized you said you were using forcedeth.  I'm unsure if the forcedeth developers maintained the same parameters.  Try it and see how it works out (obviously s/nvnet/forcedeth)

---

### Post by netztier on 2005-06-13
[QUOTE=dataw0lf]
These will force your NIC card to 100Mbps Full Duplex.
[/QUOTE]

There ain't **no good ** in setting a FastEthernet NIC to full fuplex if it's not connected to a device also configured in full fuplex mode. 

In 9 out of 10 cases, this *will* result in a duplex mismatch, because setting the duplex mode to "fixed" disables the sending of the "Fast Link Pulse" signals. 
The device at the other end however needs these to understand it's counterpart's capabilities. Not knowing what it's partner is capable of, it then has to default to half duplex, and there you go: mismatch.

So if you're connected to a hub or an unmanaged switch and you can't manually configure a port to full duplex, leave the duplex setting on "auto".

kind regards (been there, done that, twice a day...)

Marc

---

### Post by netztier on 2005-06-13
[QUOTE=smu johnson]Hi there,

But now that I've installed Ubuntu, I'm seeing extremely sluggish speeds, 1.5megs/sec from my friend.  This didn't happen in Windows either... these slow speeds.  Shut the power off and on on my router, and this didn't help at all...
[/QUOTE]

So you're saying that the same hardware with Windows instead of Ubuntu can
fill the FastEthernet pipe?

What if you use NFS, Samba or netperf?

What about the chipset driver module?

netztier.

---

