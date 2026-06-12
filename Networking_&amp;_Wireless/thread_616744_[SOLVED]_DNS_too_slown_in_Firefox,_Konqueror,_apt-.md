---
title: "[SOLVED] DNS too slown in Firefox, Konqueror, apt-get...."
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by moe_syzlak on 2007-11-18
Hey guys I need some help. Many other Linux users are having this same problem I am having, and so far there is no fix for it. DNS lookup takes too long; it averages around 5-10 seconds to lookup. But, then the page loads in under a second. I am on broadband 768k down and 128kup. It's annoying to have this fast box being slowed down by DNS lookups :mad:

I searched on some other forums and people have come up with this fix:

echo "alias ipv6 off" >> /etc/modules.conf; echo "alias net-pf-10 off" >> /etc/modules.conf.

That doesn't work. I even did the Firefox thing were I toggled "network.dns.disable.IPV6" to true with no success. 

I'm grepping the net with Google for a solution, but if you got some knowledge lay it on me. I would appreciate it alot.

---

### Post by moe_syzlak on 2007-11-18
Hey, I found something interesting on Google. Some guys over at bugs.launchpad.net in a forum came up with modifying your /etc/nsswitch.conf file - just changing one line. It works and then the network has long DNS lookups again. [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940).

---

### Post by moe_syzlak on 2007-11-18
UPDATE: I have it fixed!

I edited /etc/resolv.conf and /etc/nsswitch.conf. Backup yours and and put my info in there also I configured my router to have blank domain name. I have a picture here for you guys -> [http://www.flickr.com/photos/24601728@N00/2044442965/](http://www.flickr.com/photos/24601728@N00/2044442965/).  Then you do "sudo avahi-daemon -r". That's all I did and now I'm browsing like normal :cool:

Here is my /etc/resolv.conf:
------------------------------------<snip>-----------------------------------------------------|
search cfl.rr.com

nameserver 192.168.2.1
nameserver 65.32.5.74
nameserver 65.32.5.75
------------------------------------<snip snip>-----------------------------------------------------|

And, here is my /etc/nsswitch.conf:
------------------------------------<snip>---------------------------------------------------\
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
------------------------------------<snip snip snip>------------------------------------------------------|


update here is my /etc/modules.d/aliases file copy it and make it yours:

|---------------------------------------------------------------------------------------------|

# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 off
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

alias net-pf-16-proto-1 wire
alias net-pf-16-proto-3 ip_queue
alias net-pf-16-proto-4 tcp_diag
alias net-pf-16-proto-8 scsi_transport_iscsi
alias net-pf-16-proto-9 audit
alias net-pf-16-proto-11 cn
alias net-pf-16-proto-13 ip6_queue

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-187 irnet
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore
|-------------------------------------------|

---

### Post by racin on 2007-12-24
Thank you. This worked for me. One correction >  update here is my /etc/modules.d/aliases file copy it and make it yours:

I'm no Linux expert but I think this is supposed to be /etc/modprobe.d/aliases

---

