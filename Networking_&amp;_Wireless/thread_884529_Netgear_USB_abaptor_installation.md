---
title: "Netgear USB abaptor installation"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by mavic on 2008-08-09
Hi since some days i've received a new second hand pc. On it i've installed the last ubuntu version "8.0.4". At home to connect the pc to the internet i've only a wifi connection and the idea to carry a lan cable throw all the house in impossible. This pc dosn' t have any wifi card, so a friend gave me a wireless usb adaptor, the netgear WG117T. 
so connecting the pc direct to the router i've download wine and the usb adaptor drivers. Trubles beginns reunnig the drivers with wine on the terminal... it came the following thing:


mavic@mavic-desktop:~$ wine /home/mavic/Scrivania/WG111T_re1.2_rc1/Utility/setup.exe
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces 


For sure the installation begins but than it crash up and reading this script i can't understand why?? Can you please help me resolving this problem??? Thank for reading and for helping!

---

