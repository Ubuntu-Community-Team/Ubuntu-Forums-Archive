---
title: "Trouble with setting up an SNMP trap receiver"
date: 2024-07-19
forum: Networking &amp; Wireless
---

### Post by johnlinux28 on 2024-07-19
Hi, I'm currently trying to receive SNMP traps on my Ubuntu machine (server 24.04), using snmptrapd. I then want the service to launch a script, which will create a line of text from some of the OIDs in the trap, and then send that line of text to an other address.
I have set up the snmptrapd.conf file like so:

> authCommunity log,execute,net public
agentAddress udp:162
mibs +ALL
disableAuthorization yes
traphandle default /usr/local/bin/trap_handler.sh


trap_handler.sh is the script I want to call when a trap is received. Here is what it looks like:

```
#!/bin/bash


# Default values for sysLocation, sysContact and source
sysLocation="Unknown"
sysContact="Unknown"
source="Unknown"


# Read the SNMP trap from stdin
while read line
do
    # Extract sysLocation and sysContact from the trap
    if [[ "$line" == *"1.3.6.1.2.1.1.6"* ]]; then
        sysLocation=$(echo "$line" | awk '{print $NF}')
    fi


    if [[ "$line" == *"1.3.6.1.2.1.1.4"* ]]; then
        sysContact=$(echo "$line" | awk '{print $NF}')
    fi


    if [[ "$line" == *"UDP:"* ]]; then
        source=$(echo "$line" | awk -F'[()]' '{print $2}')
    fi
done


# Send a line of text containing sysLocation and sysContact to some address
echo "source: $source, sysLocation: $sysLocation, sysContact: $sysContact" | nc -u localhost 5555

```

Running the script itself seems to work, however when I try to send a trap nothing happens in the script's destination. I'm using the following command to simulate an SNMP trap:

> snmptrap -v 2c -c public localhost '' .1.3.6.1.6.3.1.1.5.1 .1.3.6.1.2.1.1.1.0 s "This is a test trap"

Is there something that is obviously wrong in what I'm trying to do? Also, I'm not sure how to go about debugging the whole thing, to see where something goes wrong. Any help would be greatly appreciated.

---

### Post by him610 on 2024-07-19
I did not realize how much I either forgot, or never knew.

Forgot this....
> Simple Network Management Protocol (SNMP) is an internet standard protocol that allows network devices connected over IP to be monitored and managed. It's used to communicate between devices like routers, switches, firewalls, servers, and wireless devices. SNMP is an application layer protocol that uses UDP port numbers 161/162. 

Never was aware of this...
> What is SNMP server traps?
SNMP Traps: Definition, Types, Examples, Best Practices - Netreo
An SNMP trap is a message that's sent from a network device to an SNMP management system without being solicited by the system. The trap is triggered when a specific event or condition occurs on the device, such as a link going down, an authentication or a power failure.
In my previous life, one of my jobs was a network specialist.

---

### Post by currentshaft on 2024-07-21
The script will never reach the echo line if you're always waiting for stdin in your while loop - move it inside.

---

### Post by currentshaft on 2024-07-21
> **him610 said:**
> I did not realize how much I either forgot, or never knew.

Forgot this....

Never was aware of this...

In my previous life, one of my jobs was a network specialist.

This question is really about Bash scripting and ultimately 100% irrelevant to SNMP.

---

