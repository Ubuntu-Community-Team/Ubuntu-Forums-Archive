---
title: "Samba and address resoultion"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by nivenmk1 on 2007-05-18
Greetings, first post here in a -very- long while (since Breezy!)

I've been banging my head into a wall for 4 days trying to get samba up and working, so far I believe my issue to be somewhat unique.

Samba will intermittently not see either the network, shares, other machines or both.  smbtree is giving me a headachy error when used.

My setup:
TURBO
AMD  64 3800+ (AM2)
Nforce MCP570 Chipset
7900 GS OC in SLI
500 gig SATA 3.0g/sec hdd

L-Box
AMD 2500+ Barton
Nforce 2 Chipset
7900 GS OC AGP
80 gig IDE hdd

Both running Feisty, both installed 5 days ago from most current ISO

Networking is provided by a Netgear wireless/wired router, all devices are connected via Cat5, running in full-duplex at 100 megabits.

Network Addresses:
Router: 10.0.0.1
TURBO: 10.0.0.128
L-BOX: 10.0.0.129

The Router provides DNS-lookup services via opendns.  The only entries in both machines resolv.conf files point to the router as the nameserver.  (this was done as having the opendns servers listed in resolv.conf was resulting in 15-20 second name lookup times under Firefox and ping)

On to the good stuff:

Firstly, I've used smbpasswd to successfully add my user on both machines (same username and password on both if this makes any difference)

findsmb output:
```

nivenmk1@turbo:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
10.0.0.128      TURBO         +[MSHOME] [Unix] [Samba 3.0.24]
10.0.0.129      L-BOX          [MSHOME] [Unix] [Samba 3.0.24]
nivenmk1@turbo:~$ 

```

So far so good, this output is replicated when running findsmb on the other machine (l-box)

smbtree output:
```

nivenmk1@turbo:~$ smbtree
Password: 
MSHOME
        \\TURBO                         turbo server (Samba, Ubuntu)
                \\TURBO\IPC$            IPC Service (turbo server (Samba, Ubuntu))
                \\TURBO\print$          Printer Drivers
        \\L-BOX                         L-Box server (Samba, Ubuntu)
timeout connecting to 208.69.32.130:445
timeout connecting to 208.69.32.130:139
Error connecting to 208.69.32.130 (Operation already in progress)
cli_start_connection: failed to connect to L-BOX<20> (208.69.32.130)

```

Both of the machines report the same series of error messages when running smbtree, both trying to connect to the same two addresses before the error messages and a dump back to the prompt.

On L-BOX, the final line in the smbtree trainwreck is occasionally "failed tcon_X with NT_STATUS_ACCESS_DENIED"

As you can see above, this address isn't on the LAN connecting the two machines.  I haven't been able to find out where it is resolving the address to the erroneous IP but I believe this to be a majority of the problem I'm having.

These errors (including bad behavior from the network window) occur no matter what I'm sharing (or not sharing) on either machine.

The only other thread I've seen on the forums with a similar output from smbtree was discontinued because the "helpee" wasn't cooperating with the helper to the point at which the helper got frustrated and stopped assisting.  This thread can be found [here]("http://ubuntuforums.org/showthread.php?t=374292&highlight=208.69.32.130").

So far I've tried:
-Completely removing anything smelling of samba (samba, smbfs, smbclient and the like) using synaptic's complete removal option. Then reinstalling it all through synaptic.
-mounting using smbmount, this works erratically
-connecting via Places->Connect to server...  This resulted in a connection with old shares which could not be accessed.  New shares would not appear on this connection after it was created, even if both machines were restarted.
-adding in winbind to [as it ends up not] resolve the lookup issue between the machines
-searching the forums till I'm blue in the face and posting this thread :)

Any help or ideas would be most appreciated.

---

### Post by nivenmk1 on 2007-05-18
A little update here:

My third machine:
LAPPY
Compaq Presario R3000 notebook
Windows XP (yay ATI integrated Radeon)

So as it turns out, LAPPY can see the shares on both L-BOX and TURBO and communicate without a problem both reading and writing files.

However, both ubuntu machines, L-BOX and TURBO, cannot see any network shares on any machine (to include LAPPY).

Helpz!

---

### Post by nivenmk1 on 2007-05-18
Nother update:

O.K. so I'm half retarded.

As it ends up 208.69.32.130 is  nxdomain.guide.opendns.com

For the time being, I've made entries in /etc/hosts to point to the peer machines on the network.  After making these changes on TURBO, here's the result of smbtree:
```

nivenmk1@turbo:~$ smbtree
Password: 
MSHOME
        \\TURBO                         turbo server (Samba, Ubuntu)
                \\TURBO\print$          Printer Drivers
                \\TURBO\IPC$            IPC Service (turbo server (Samba, Ubuntu))
        \\LAPPY                         Lappy
                \\LAPPY\Printer         Microsoft Office Document Image Writer
                \\LAPPY\Emule          
                \\LAPPY\SharedDocs     
                \\LAPPY\print$          Printer Drivers
                \\LAPPY\IPC$            Remote IPC
        \\L-BOX                         L-Box server (Samba, Ubuntu)
                \\L-BOX\print$          Printer Drivers
                \\L-BOX\Emule   
                \\L-BOX\IPC$            IPC Service (L-Box server (Samba, Ubuntu))
nivenmk1@turbo:~$ 
```

And furthermore, now that address resolution is out of the way for network-transactions-by-box-name, everything can share as needed.

The question I have which remains is this:
Why is it that samba had a problem with this on my network, when a buddy of mine with a very similar setup experienced none of the setup issues?

Other than that, we're gonna call this myth busted.

---

### Post by kWahab on 2007-05-30
I have the exact same problem when i add OpenDNS server ip's to my D-Link router, but when i use my ISP provided server addresses everything works smoothly.

Cannot use the /etc/hosts trick as i have to use dynamic ip for my laptop.

---

### Post by Healey on 2007-06-17
Hi

I think I have the same problem with samba

Can somebody explain what changes need to be made to /etc/hosts in order for me to see my shared folders and share a printer.

It all worked perfectly in Dapper but since I started using Feisty its no good at all

I also found this info :
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)

It talks about downgrading samba to a previous version - Problem is I dont know how to do that !!.  I also notice that there is a newer version of samba on their website - I dont know how to install that either.


Could this bug be the problem ???

I am a bit of a newbee so please make it as easy as possible 

Best Regards and Thanks

Healey

---

