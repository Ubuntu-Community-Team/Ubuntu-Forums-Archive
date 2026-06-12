---
title: "SMB-NAT Problems"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Dudeman02379 on 2008-04-11
I installed SMB-NAT from synaptic package manager.  When I try to run it against a machine I get

[*]--- Attempting to connect with name: *********
[*]--- CONNECTED with name: *********
[*]--- Attempting to connect with protocol: MICROSOFT NETWORKS 1.03
[*]--- Server time is Fri Apr 11 14:49:00 2008
[*]--- Timezone is UTC-4.0
[*]--- Remote server wants us to encrypt, telling it not to
[*]--- Attempting to establish session

[*]--- Attempting to access share: \\*********\
[*]--- Unable to access
Segmentation fault (core dumped)

I put in the stars where the computers name would be.  I am doing this from a virtual machine and I am targeting another virtual machine.  Does anyone know why this would happen?  Please let me know if you need more information.  THANKS!!!!

EDIT:
I have been doing more and more reading about this tool.  I guess it is not ideal to be used against a windows xp machine.  Is there another similar tool to bruteforce a smb username/password on a windowsxp share?  FYI this is all being done in a lab on virtual machines that I created and own.  I work for a network consulting company and we are trying to develop some good pentests for our clients.  Thanks again!

---

### Post by hoffmannick on 2008-05-13
One great tool is smbbf, it's pre-installed on BackTrack2 (for some reason it's not included on Backtrack3).  It'll bruteforce SMB passwords very very quickly.  I have yet to compile and install it on Ubuntu though.....

---

