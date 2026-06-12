---
title: "Unable to Connect PPTP using 14.04 on VPS Error 734"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by james40 on 2015-09-02
Hi all,
I cant seem to get my PPTP connection to work. I have already manged an OpenVPN server I'm setting up PPTP purely for convince so friends and family who I am not close enough to setup OpenVPN credentials for. While OpenVPN works just fine however when trying to connect to PPTP I get

[COLOR=#6A6A6A][FONT=arial]**Error 734**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: The PPP link control protocol was terminated.

The messages log doesn't tell me much either

[/FONT][/COLOR]```
pppd[12517]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
pppd[12517]: pppd 2.4.5 started by <SYSUSER>, uid 0
pppd[12517]: Using interface ppp0
pppd[12517]: Connect: ppp0 <--> /dev/pts/2
pppd[12517]: peer from calling number <CLIENT IP> authorized
pppd[12517]: Connection terminated.
pppd[12517]: Connect time 0.1 minutes.
pppd[12517]: Sent 0 bytes, received 0 bytes.
pppd[12517]: Exit.



```

I followed this guide [https://vpnreviewer.com/how-to-install-vpn-server-pptp-debian-ubuntu-linux-vps](https://vpnreviewer.com/how-to-install-vpn-server-pptp-debian-ubuntu-linux-vps)

So I've tried both the default and the following pptpd-option configuration

```
name pptpd refuse-pap
 refuse-chap
 refuse-mschap
 require-mschap-v2
 require-mppe-128
 ms-dns 8.8.8.8
 #ms-dns 8.8.4.4
 proxyarp
 nodefaultroute
 lock
 nobsdcomp
 mtu 1490
 mru 1490
```

My chap-secrets is as follows
```
<USERNAME> pptpd <PASS> *
```

Which seems to work because if I deliberately put in the wrong password the log file changes to this:

```
pppd[14156]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.pppd[14156]: pppd 2.4.5 started by <SYSUSER>, uid 0
pppd[14156]: Using interface ppp0
pppd[14156]: Connect: ppp0 <--> /dev/pts/2
pppd[14156]: Peer <USER> failed CHAP authentication
pppd[14156]: Connection terminated.
pppd[14156]: Exit.
```

Thanks for any help in advance!

---

### Post by james40 on 2015-09-02
Oops I thought I put this in Networking Category. Can an admin please move this if possible?

---

### Post by howefield on 2015-09-03
> **james40 said:**
> Oops I thought I put this in Networking Category. Can an admin please move this if possible?

Done.

---

### Post by james40 on 2015-09-06
Not sure if this helps but this is the Log from Windows:

```
[COLOR=#000088][15632] 09-07 11:12:53:820: GetParamsListFromLsa Default=0[/COLOR][15632] 09-07 11:12:53:822: GetParamsListFromLsa. 0x0
[15632] 09-07 11:12:53:824: CreateConnection: entry=VPN Connection 2, pbk=C:\Users\[USER]\AppData\Roaming\Microsoft\Network\Connections\Pbk\rasphone.pbk
[15632] 09-07 11:12:53:824: CreateConnection: fSecureRoutingCompartment: 0 and dwConSessionId 1  old Compartment ID 1:
[15632] 09-07 11:12:53:824: SetRasmanServiceStopControl: Enabled 0
[15632] 09-07 11:12:53:825: CreateConnection: Created new connection. hconn=0x1e0000, ref=1, pConn=0x146924b0
[15632] 09-07 11:12:53:833: IsTrustedCustomDll: pwsz=, fTrusted=0, rc=0
[15632] 09-07 11:12:53:834: PortOpenEx: WAN Miniport (PPTP)
[15632] 09-07 11:12:53:841: SetRasmanServiceStopControl: Enabled 0
[15632] 09-07 11:12:53:841: PortOpen (2, VPN3-1) OpenInstances = (0)
[15632] 09-07 11:12:53:841: d:\w7rtm\net\rras\ras\rasman\rasman\request.c: 2757: port 2 state chg: prev=4, new=4
[15632] 09-07 11:12:53:841: PortOpenEx (2) : OpenInstances = 1
[15632] 09-07 11:12:53:841: PortOpenEx: rc=0x0. DeviceFound=1
[15632] 09-07 11:12:53:842: CleanUpDeadClientProcessBlock
[15632] 09-07 11:12:53:843: SetDialMachineEventHandleCommon:
[15632] 09-07 11:12:53:843: Cleaning up process 14124
[15632] 09-07 11:12:53:843: CleanUpEventQueue:
[15632] 09-07 11:12:53:843: AddConnectionPort: pConn=0x146924b0, pConn->CB_Ports=1, port=2, dwSubEntry=1
[15632] 09-07 11:12:53:861: SetTunnelEndPoints: Port=2,SourceAddr=[INTERNAL IP],DestinationAddr=[PPTP SERVER IP],IfIndex=20
[15632] 09-07 11:12:53:861: SetTunnelEndPoints: Not setting source end point as Tunnel is PPTP/SSTP
[3616] 09-07 11:12:53:881: d:\w7rtm\net\rras\ras\rasman\rasman\util.c: 2647: port 2 state chg: prev=4, new=0
[3616] 09-07 11:12:53:881: d:\w7rtm\net\rras\ras\rasman\rasman\util.c: 2692: port 2 async reqtype chg: prev=0, new=15
[3616] 09-07 11:12:53:881: Adding timeout of 120 for listen
[3616] 09-07 11:12:53:884: DwSendNotificationInternal(ENTRY_CONNECTING) rc=0x00000000
[3616] 09-07 11:12:53:884: Connect request on port: VPN3-1, error code 600
[5988] 09-07 11:12:54:657: WorkerThread: Async work event signaled on port: VPN3-1
[5988] 09-07 11:12:54:657: OVEVT_DEV_ASYNCOP. pOverlapped = 0xd564c00
[5988] 09-07 11:12:54:657: CompleteAsyncRequest: pOverlapped=0xad53780
[5988] 09-07 11:12:54:657: PostDialEventContext:  for pid:0x372c, client Event:0x16f4context pointer=0xad53780, type=2
[5988] 09-07 11:12:54:657: AppendNewMsgToQueue:Set client Event:0x16f4
[5988] 09-07 11:12:54:657: Inside DeviceListenRequest NumParams 3
[5988] 09-07 11:12:54:657: Found DEV_SPECIFIC_INFO_KEY: Size:16 Offset:133
[5988] 09-07 11:12:54:657: Correlation Guid is {E2B364C5-A7BA-4B04-A5ED-A1660A497FBB}
[5988] 09-07 11:12:54:657: d:\w7rtm\net\rras\ras\rasman\rasman\worker.c: 2580: port 2 async reqtype chg: prev=15, new=0
[5988] 09-07 11:12:54:657: ServiceWorkRequest: Async op event 15 for port VPN3-1 returned 0
[19856] 09-07 11:12:54:657: PickOneMsgForAEvent:send context to Pid:0x372c, clientEvent:0x16f4
[19856] 09-07 11:12:54:657: PickOneMsgFromQueueList:
[19856] 09-07 11:12:54:661: ConnectCompleteRequest: entered for port 2
[19856] 09-07 11:12:54:662: d:\w7rtm\net\rras\ras\rasman\rasman\request.c: 7905: port 2 state chg: prev=0, new=2
[19856] 09-07 11:12:54:662: AllocBundle: pBundle=0x184be290

[19856] 09-07 11:12:54:662: d:\w7rtm\net\rras\ras\rasman\rasman\request.c 9172: Mapping Cookie to handle. port = VPN3-1(0xd5664f0), Bundlehandle = 0x27, linkhandle = 0x27
[19856] 09-07 11:12:54:662: Connection Completed on port: VPN3-1, error code: 0
[19856] 09-07 11:12:54:668: ProtocolStart: PbkPath: C:\Users\[USER]\AppData\Roaming\Microsoft\Network\Connections\Pbk\rasphone.pbk
[19856] 09-07 11:12:54:668: ProtocolStart: EntryName: VPN Connection 2
[19856] 09-07 11:12:54:668: ProtocolStart: PhoneNum: [PPTP SERVER IP]
[19856] 09-07 11:12:54:668: GetParamsListFromLsa Default=0
[19856] 09-07 11:12:54:669: GetParamsListFromLsa. 0x0
[19856] 09-07 11:12:54:669: ProtocolStart: UserName: [PPTP USERNAME]
[19856] 09-07 11:12:54:669: ProtocolStart: Domain: 
[19856] 09-07 11:12:54:669: DwCacheCredMgrCredentials
[19856] 09-07 11:12:54:670: DwCacheCredMgrCredentials: 0x0
[10828] 09-07 11:12:54:671: ProtocolStarted...VPN3-1
[10828] 09-07 11:12:58:088: SendProtocolResultToRasman: msgid=1
[10828] 09-07 11:12:58:088: Setting last error for port VPN3-1 to ppp error 0x2de
[10828] 09-07 11:12:58:088: SetProtocolResultAvailableEvent: pOverlapped=0xad537b8
[10828] 09-07 11:12:58:088: PostDialEventContext:  for pid:0x372c, client Event:0x16f4context pointer=0xad537b8, type=3
[10828] 09-07 11:12:58:088: AppendNewMsgToQueue:Set client Event:0x16f4
[15596] 09-07 11:12:58:088: PickOneMsgForAEvent:send context to Pid:0x372c, clientEvent:0x16f4
[15596] 09-07 11:12:58:088: PickOneMsgFromQueueList:
[15596] 09-07 11:12:58:091: CleanUpDeadClientProcessBlock
[15596] 09-07 11:12:58:091: SetDialMachineEventHandleCommon:
[15596] 09-07 11:12:58:091: SetDialEventHandleCommon: posting last event for port 2
[15596] 09-07 11:12:58:091: PostDialEventContext:  for pid:0x372c, client Event:0x16f4context pointer=0xad537f0, type=4
[15596] 09-07 11:12:58:091: PostDialEventContext: going to put the  OVEVT_DIAL_LAST message in the queue

[15596] 09-07 11:12:58:091: AppendNewMsgToQueue:Set client Event:0x16f4
[10828] 09-07 11:12:58:092: SendProtocolResultToRasman: msgid=10
[10828] 09-07 11:12:58:092: PROTOCOL_RES_Stopped. dwError=0x2de
[10828] 09-07 11:12:58:092: setting error to 734
[10828] 09-07 11:12:58:092: DwProcessProtocolFailureMessage: disconnecting VPN3-1,hEventClientDisconnect=0xffffffff
[10828] 09-07 11:12:58:092: Disconnecting Port 0xVPN3-1, reason 0
[10828] 09-07 11:12:58:092: DisconnectPort: Saving Bundle stats for port VPN3-1
[COLOR=#000088][10828] 09-07 11:12:58:092: QueueCloseConnections: no dependent connections[/COLOR]
```

---

