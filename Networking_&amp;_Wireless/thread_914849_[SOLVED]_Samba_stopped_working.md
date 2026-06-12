---
title: "[SOLVED] Samba stopped working"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by ehamman on 2008-09-09
I've been having a lot of fun changing from Windows to Ubuntu.
Was very pleased to get a small network set up for home with Samba - printing and file transfer working over Wi-Fi and Ether.
However, now my Samba has 'stopped' working.  I've tried to figure out from other posts what is wrong, but get either sidetracked or lost.  A short history of what has been done on my computer.

I got the IP_ports thingy running under Firestarter - I checked the network when I set this up, and it worked then.
I deleted some garble from the network hosts table - stuff that started with ::f???? 
I had trouble with Hobbit client not working and had to delete some hobbit-client config file data to get rid of it [Part of an unsuccessful attempt to see my Linux machine from Windows.]
From the other posts I checked the following:
Samba config file - still the same
I installed a bunch of add-ons for Firefox  :)  [I reckon its not this]
Changing the password for the "user" under which the hosted directories are listed - I get the following message:

cli_pipe_validate_current_pdu: RPC fault code DCERPC_FAULT_OP_RNG_ERROR received from remote machine 127.0.0.1 pipe \samr fnum 0x7191!
machine 127.0.0.1 rejected the password change: Error was : NT code 0x1c010002.

So, now I am stuck.  Any help will be much appreciated.

---

### Post by ehamman on 2008-09-10
Well, it seems I managed to get it working again.
Somehow the outgoing traffic in Firestarter got cleared and my DNS server address changed in the Network settings.
I'd hate to think what someone with no computer experience would have done.
Probably not so much fidgeting :lolflag:
So for future reference - If Samba stop working - check the network settings and always keep record of what you do.
Which begs the question - is there a system restart point that you can set up, except the out-of-the-box one?

---

