---
title: "Automatic network scripts not running?"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by ieatkittens on 2007-11-04
I have two scripts...one designed to mount a server via SSHFS on network start, and another to auto unmount to on network disconnect.

The scripts work flawlessly if I manually run them, but the script files  /etc/network/if-up.d/mountsshfs and /etc/network/if-down.d/umountsshfs don't run automatically!

Is there any reason why these scripts wouldn't automatically run?

---

### Post by DarkN00b on 2007-11-04
It could be that your scripts are trying to run too early. Try putting

```
sleep 20s
``` 

as the first line after #!/bin/sh. This will tell your scripts to wait 20 seconds to run.

---

### Post by ieatkittens on 2007-11-05
Sleeping doesn't seem to help...

it's strange, the scripts run perfectly when I run them manually, but they never run when I connect or disconnect to a network.

Are the scripts only run when the interface is brought up  or down or are they run when a connection is made?

---

### Post by tkharris on 2007-11-05
What are the permissions on the script?

```

chmod 750 script
chown root.wheel script

```

---

