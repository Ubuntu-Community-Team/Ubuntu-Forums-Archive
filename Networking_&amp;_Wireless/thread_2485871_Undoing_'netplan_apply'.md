---
title: "Undoing 'netplan apply'"
date: 2023-04-12
forum: Networking &amp; Wireless
---

### Post by jackbuff on 2023-04-12
I have a computer that requires that I set up some of its ethernet ports to have static IP addresses.   The method that these computers were originally configured was to create a config.yaml file which then is applied with 'sudo netplan apply'. We recently bought some new computers that have different network interfaces.  I configured what I could at the office and tested what I could but the only way to know for sure that things are working is to put it into a machine and check to see if it is actually working.   In my case, the machine is in a different country than I am in and I can't connect this computer to the internet to remote into it.  I do have someone who can type things in and relay to me what the results are though. 

When setting up these computers, after having done 'sudo netplan apply', I have noticed that the normal ways that one would manage network connections don't work anymore such as seeing when a cable is plugged in through the network manager, or on the menu bar where the networking settings show up when there are connections available.     On the command line, if I plug something in which should serve an IP address and type 'ip a', I no-longer see a connection.   

What I would like to do is switch back to how things were upon a clean install of Ubuntu as far as networking is concerned where all ports are dhcp and I can use the network manager.   After figuring a few things out in that state, I would like to go back to how things are now, though with a few fixes.   Presumably, I would just once again do 'sudo netplan apply'.  

* How can I go back to factory default settings?  
* If there are multiple ways, what would be the easiest to relay to someone who is technical but doesn't know Linux?  He knows how to get to a terminal.

For reference, this computer is using Ubuntu 18.04 on an Intel Processor.

---

### Post by #&amp;thj^% on 2023-04-12
I wondered when this topic would come about, I'll let others provide with suggestions.
See the Known Issues portion of the netplan-apply manpage:

KNOWN ISSUES
       > netplan  apply will not remove virtual devices such as bridges and bonds that have been created,
       even if they are no longer described in the netplan configuration.  That is due to the fact that
       netplan operates statelessly and is not aware of the previously defined virtal devices.

       This  can  be  resolved  by manually removing the virtual device (for example ip link delete dev
       bond0) and then running netplan apply, by rebooting, or by creating a temporary  backup  of  the
       YAML  state in /etc/netplan before modifying the configuration and passing this state to netplan
       (e.g.  mkdir -p /tmp/netplan_state_backup/etc &&  cp  -r  /etc/netplan  /tmp/netplan_state_back&#8208;
       up/etc/ then running netplan apply &#8211;state /tmp/netplan_state_backup)

I'm still using ifupdown on some of mine, less cluttered.

---

