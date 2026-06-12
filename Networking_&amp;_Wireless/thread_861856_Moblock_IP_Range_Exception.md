---
title: "Moblock IP Range Exception"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Xd3viance on 2008-07-17
Hi,

I'm using Hardy AMD64 and had Moblock working just fine. An update of Moblock that was pushed out now says that the previous method for white listing IP ranges will be depreciated in some future version. I was using the WHITE_IP_IN and WHITE_IP_OUT method to specify IP ranges I want to white list. It now tells me when I do a moblock-control start that I should now use the 'allow list' instead. How can I do this?

Thanks!

---

### Post by jre on 2008-07-17
> **Xd3viance said:**
> It now tells me when I do a moblock-control start that I should now use the 'allow list' instead. How can I do this?
First off: Note that **currently** your old entries still work! When I completely remove the WHITE_IP_ stuff I will add its content automatically to the allow list.

To do it manually you have to do the following:
If you had these entries:
```
WHITE_IP_OUT="123.123.123.123 192.168.0.0/24"
WHITE_IP_IN="123.123.123.123 234.234.234.234"
```

Then you have to add these lines to /etc/moblock/allow.p2p
```
Any description:123.123.123.123-123.123.123.123
My LAN:192.168.0.0-192.168.0.255
Another description:234.234.234.234-234.234.234.234
```

If you want to use seperate allow lists for incoming/outgoing/forward connections then you first have to edit this part in moblock.conf:
```
# The path to the allow lists
# Note that per default the same allow list is used for all (in, out and
# forwarded) connections.
# The path to the allow list for incoming connections
ALLOW_IN="$CONF_DIR/allow.p2p"
# The path to the allow list for outgoing connections
ALLOW_OUT="$CONF_DIR/allow.p2p"
# The path to the allow list for forwarded connections
ALLOW_FW="$CONF_DIR/allow.p2p"
```

Feel free to ask further questions or give any other feedback ;-)
jre

---

### Post by Xd3viance on 2008-07-17
Thanks jre, that was exactly what I was looking for! Upon starting|stopping|reloading Moblock, I no longer receive the message that I'm whiting IPs in a way that will be depreciated.

---

### Post by jre on 2008-07-17
A question of a non-native English speaker:
Is it "deprecated" or "depreciated" for something that is old and will soon be removed?
I tend to the latter but the web seems to prefer the first ;-)

---

### Post by Mud.Knee.Havoc on 2008-09-12
> **jre said:**
> A question of a non-native English speaker:
Is it "deprecated" or "depreciated" for something that is old and will soon be removed?
I tend to the latter but the web seems to prefer the first ;-)

Although similar, the words are not the same.

"Deprecated" means phased out.
"Depreciated" means reduced in value.

---

