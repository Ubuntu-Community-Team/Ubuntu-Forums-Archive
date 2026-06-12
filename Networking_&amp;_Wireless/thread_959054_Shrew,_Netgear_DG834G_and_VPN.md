---
title: "Shrew, Netgear DG834G and VPN"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by 77_Chris on 2008-10-26
Hi!

I need a little help connecting to my network via vpn from an ubuntu 8.10 laptop.

Currently I've installed Shrew on the mobile machine, but any other suitable vpn-client is also welcome.

The actual situation:

Following messages in the router's log-file:

Sun, 2008-10-26 08:45:19 - [xxxxxxx] responding to Main Mode from unknown peer 192.168.0.x
Sun, 2008-10-26 08:45:20 - [xxxxxxx] sending notification PAYLOAD_MALFORMED to 192.168.0.x:500
Sun, 2008-10-26 08:45:30 - [xxxxxxx] STATE_MAIN_R2: retransmission; will wait 20s for response

The router (Netgear DG834G) is set to use 3DES and a pre-shared key, PFS is activated.

The Shrew-client uses the following settings:

General:
- use a virtual adapter and obtain it automatically
- configuration method is pull

Client:
- NAT-traversal is disabled
- IKE fragmentation is enabled
- Dead Peer Detection is enabled
- IKSAMP failure notifications are enabled
- Client Login Banner is enabled

Name Resolution:
- DNS enabled (automatic)

Authentication:
- Authentication Method: Mutual OSK
Local Identity:
- Identification Typ: IP Address
Remote Identity:
- Identification Typ: IP Address
Credentials:
- preshared key entered

Phase 1:
- exchange type: main
- DH exchange: auto
- cipher algorithm: 3des
- hash algorithm: auto
- key lifetime time lim: 86400
- key lifetime data lim: 0

Phase 2:
- Transform algorithm: 3des
- HMAC algorithm: auto
- PFS exchange auto
- compression algorithm: disabled
- key lifetime time lim: 3600
- key lifetime data lim: 0

Policy:
- set to obtain it automatic

Thanks a lot in advance,
Chris

---

### Post by 77_Chris on 2008-10-29
Nobody?

---

### Post by steveparbkk on 2009-04-25
Hi,

This is the same scenario I have. My home has a Netgear DG834 and I have Eeebuntu 8.10 on my EeePC.  I would like to get my EeePC to connect to my home network over VPN.

Netgear has a lot of information about setting up the DG834 as a VPN server (i've saved numerous links so message me if you want them although they are to find), along with comprehensive settings that need to be configured.  I can't find where to enter these numerous settings in the network manager.  I've just installed Shrew and will take a look at that.

I wonder if anyone has had any success with this permutation.

Steve

---

### Post by steveparbkk on 2009-04-30
I wonder if you found a solution 77_Chris?  I managed to get passed the problem you experienced.  This issue is an authentication problem.  The Shrew VPN client sends the internal IP address as its identification whereas the DG834G is expecting the external IP address.

I tricked the DG834G by changing the setting in the Shrew VPN client. Under the Local identity tab of the Authentication Tab I unchecked the 'Use discovered local host address' field and added the external IP address in the data field.  In my DG834G log file I now get:

Thu, 2009-04-30 12:36:22 - [MiniEee] responding to Main Mode from unknown peer 58.8.195.60
Thu, 2009-04-30 12:36:22 - [MiniEee] sent MR3, ISAKMP SA established
Thu, 2009-04-30 12:36:22 - [MiniEee] Dead Peer Detection (RFC 3706): enabled
Thu, 2009-04-30 12:40:33 - [MiniEee] received Delete SA payload: deleting ISAKMP State #3

Trouble is that, as evidenced by the last entry in the log file extract above, the process breaks down at which point the Shrew Client reports 'gateway is not responding'.

I need to resolve this issue so any additional information you might have would be helpful.

Thanks,
Steve

---

### Post by fcigoi on 2009-06-14
Same problem here, although with another router.

I have been trying to connect from a laptop running Jaunty via a UMTS connect card to my router at home. In fact I started with a Netgear FVS114 and then moved on to an FVS338, but the results are still the same, i.e. the connection times out during negotiation. The only difference being the fact that while the FVS114 used to hang up completely after the aborted attempt, the FVS338 has no problem, but still no connection.
for both attempts I have used the configuration described on the Shrewsoft support page for connection with a Netgear router, using the same parametres, but to no avail.
Has any of you discovered anything more ?

Grateful for any ideas

---

### Post by steveparbkk on 2009-06-14
Hi fcigoi,

Shrew has a fairly active support Mailing list [ here]("http://www.shrew.net/support").  They even have a 'How To' for the Netgear FVS33x [here]("http://www.shrew.net/support/wiki/HowtoNetgear").

I didn't manage to resolve my issue yet.  I have to refer to the RFCs to identify whether it is the Shrew Client or the Netgear router that is non-compliant.  Currently my hunch is that it's the Netgear, but I need to find time to read the technical papers to be in a better position to make my case forcefully in the Netgear forums.

I suspect that if you can use Aggressive Mode instead of Main Mode, which my Netgear router doesn't facilitate, you should be able to get them to work together.

Please let me know how you get on as one strategy I am considering is replacing my DG834 for a higher spec. Netgear router at one location and I don't want to purchase a superfluous router.

Good luck!

---

### Post by fcigoi on 2009-06-15
Well, the way I started, knowing very little of VPNs, is exactly that how-to you mentioned.
Also, since I had and FVS114 when I started trying, and it didn't work, I had the doubt that the how-to was a "338 only", so I upgraded to FVS338, but the result is still the same.
My main problem is that most technical papers from Netgear refer to Windows clients, and it's very difficult to compare those with Linux clients such as Shrew, especially as they use slightly different terminology to describe the same parameters.
I'll keep trying...

---

### Post by steveparbkk on 2009-06-15
fcigoi,

From my very limited understanding of VPN, the key is reading the messages in the logs.  I've read various papers on this subject though I can't really remember much of the detail now, but I believe there are about three distinct stages in establishing a VPN connection.  In order to troubleshoot you need to establish at what stage of the process that it is failing.  [This]("http://www.vpncasestudy.com/download/troubleshoot/Troubleshooting_IKE_VPN.pdf") might be helpful.

You and I share a common goal.  I am committed to getting my Ubuntu box to connect to my Netgear router (or a higher spec Netgear router) using VPN.  Have you tried the Netgear forums?  With your Netgear router I believe you can gain access to the Netgear ProSecure Community (for what its worth), which I can't with my cheapy DG834.

Out of interest, did you follow the How To exactly?  Did you check that you have the latest firmware installed?

With regard to terminology, my understanding is that Netgear is a member of [this]("http://www.vpnc.org/") body, which ought to mean that they use standardised terminology, no? Assuming you can decipher the logs you that should enable you to determine how and why you were unable to establish a connection.  I have found Matthew Grooms on the Shrew help list to be very helpful and willing to answer some of the very basic questions I've posed on the list.  I believe you are quite right that the solution lies in getting technical.

I'm particularly interested in your progress.  Please keep me informed.

Good luck!

---

