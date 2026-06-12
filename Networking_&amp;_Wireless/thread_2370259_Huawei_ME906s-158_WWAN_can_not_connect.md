---
title: "Huawei ME906s-158 WWAN can not connect"
date: 2017-09-01
forum: Networking &amp; Wireless
---

### Post by rupert2 on 2017-09-01
Helo
In my Thinkpad x260 I have Huawei ME906s-158 WWAN card. I can not establish connection although it shows signal strength in network manager. I read some threads, tried to solve problem, but with no luck :-(.
My system:
```
uname -a
Linux ThinkPad-X260 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

I upgraded some libraries:
libmbim-glib4 - 1.14.0-2
libqmi-glib5 - 1.18.0-2
modemmanager - 1.6.8.1
usb_modeswitch - 2.5.1

The device has three configurations, the third one is MBIM. With latest usb_modeswitch I can switch them. I tried configuration 2 (default) and 3 (MBIM).

```
mmcli -L


Found 1 modems:
        /org/freedesktop/ModemManager1/Modem/4 [Huawei] MBIM [12D1:15C1]


sudo mmcli -m 4


/org/freedesktop/ModemManager1/Modem/4 (device id 'fa5d37a1274bd3bc2bb77d42b31a40c3cad3a57b')
  -------------------------
  Hardware |   manufacturer: 'Huawei'
           |          model: 'MBIM [12D1:15C1]'
           |       revision: '11.617.04.00.00'
           |      supported: 'gsm-umts, lte'
           |        current: 'gsm-umts, lte'
           |   equipment id: '867160024262606'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3'
           |        drivers: 'cdc_mbim, option1'
           |         plugin: 'Huawei'
           |   primary port: 'cdc-wdm1'
           |          ports: 'ttyUSB0 (at), cdc-wdm1 (mbim), wwp0s20f0u3c3 (net)'
  -------------------------
  Numbers  |           own : 'unknown'
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'unknown (2)'
           |          state: 'registered'
           |    power state: 'on'
           |    access tech: 'lte'
           | signal quality: '0' (cached)
  -------------------------
  Modes    |      supported: 'allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: 2g, 3g, 4g; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  3GPP     |           imei: '867160024262606'
           |  enabled locks: 'none'
           |    operator id: '26001'
           |  operator name: 'Plus'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/4'


  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/29'



```

```
sudo mmcli -L


Found 1 modems:
        /org/freedesktop/ModemManager1/Modem/3 [Huawei Technologies Co., Ltd.] ME906s-158




sudo mmcli -m 3


/org/freedesktop/ModemManager1/Modem/3 (device id '8011cc1082047f338b90ee52a7514a1afbde0035')
  -------------------------
  Hardware |   manufacturer: 'Huawei Technologies Co., Ltd.'
           |          model: 'ME906s-158'
           |       revision: '11.617.04.00.00'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
           |   equipment id: '867160024262606'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3'
           |        drivers: 'option1, cdc_ether'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB0'
           |          ports: 'ttyUSB0 (at), enp0s20f0u3c2 (net), ttyUSB2 (at), ttyUSB3 (at)'
  -------------------------
  Numbers  |           own : 'unknown'
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (2), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'connecting'
           |    power state: 'on'
           |    access tech: 'lte'
           | signal quality: '87' (recent)
  -------------------------
  Modes    |      supported: 'allowed: 4g; preferred: none
           |                  allowed: 3g; preferred: none
           |                  allowed: 2g; preferred: none
           |                  allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: 2g, 3g, 4g; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4'
  -------------------------
  3GPP     |           imei: '867160024262606'
           |  enabled locks: 'none'
           |    operator id: '26001'
           |  operator name: 'Plus'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/3'


  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/26'



```

Log when set to configuration 2
```
Sep  1 11:12:22 ThinkPad-X260 NetworkManager[988]: <debug> [1504257142.6709] device[0x211b850] (wlp4s0): add_pending_action (1): 'scan'
Sep  1 11:12:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257143.4661] device[0x211b850] (wlp4s0): remove_pending_action (0): 'scan'
Sep  1 11:12:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257143.4847] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:12:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257143.4859] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3065] active-connection[0x219e220]: set device "ttyUSB0" [0x21de800]
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3066] device[0x21de800] (ttyUSB0): add_pending_action (1): 'activation::0x219e220'
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3069] active-connection[0x219e220]: constructed (NMActRequest, version-id 18)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3072] auth: call[72]: CheckAuthorization(org.freedesktop.NetworkManager.network-control), subject=unix-process[pid=1358, uid=1000, start=1355]
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3141] auth: call[72]: CheckAuthorization succeeded: (is_authorized=1, is_challenge=0)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <info>  [1504257149.3164] device (ttyUSB0): Activation: starting connection 'Plus' (4b77e7b1-a7fc-49db-8cb3-7b516041aaf7)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3165] device[0x21de800] (ttyUSB0): activation-stage: schedule activate_stage1_device_prepare,2 (id 12834)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <info>  [1504257149.3170] audit: op="connection-activate" uuid="4b77e7b1-a7fc-49db-8cb3-7b516041aaf7" name="Plus" pid=1358 uid=1000 result="success"
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3173] device[0x21de800] (ttyUSB0): activation-stage: invoke activate_stage1_device_prepare,2 (id 12834)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <info>  [1504257149.3174] device (ttyUSB0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3178] active-connection[0x219e220]: set state activating (was unknown)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3179] active-connection[0x219e220]: check-master-ready: not signalling (state activating, no master)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3182] (ttyUSB0): launching connection with ip type 'ipv4' (try 1)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3185] device[0x21de800] (ttyUSB0): activation-stage: complete activate_stage1_device_prepare,2 (id 12834)
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3199] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:12:29 ThinkPad-X260 NetworkManager[988]: <debug> [1504257149.3203] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect started...
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (4/8): Wait to get fully enabled
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (5/8): Register
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (6/8): Bearer
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (7/8): Connect
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/1: state changed (registered -> connecting)
Sep  1 11:12:29 ThinkPad-X260 ModemManager[5529]: <warn>  Couldn't find associated cdc-wdm port for 'net/enp0s20f0u3c2'
Sep  1 11:13:10 ThinkPad-X260 NetworkManager[988]: <debug> [1504257190.6392] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:13:10 ThinkPad-X260 NetworkManager[988]: <debug> [1504257190.6458] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
Sep  1 11:13:25 ThinkPad-X260 NetworkManager[988]: <debug> [1504257205.6704] device[0x211b850] (wlp4s0): add_pending_action (1): 'scan'
Sep  1 11:13:26 ThinkPad-X260 NetworkManager[988]: <debug> [1504257206.4608] device[0x211b850] (wlp4s0): remove_pending_action (0): 'scan'
Sep  1 11:13:30 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/1: state changed (connecting -> registered)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <warn>  [1504257210.6745] (ttyUSB0): failed to connect modem: Connection attempt timed out
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <info>  [1504257210.6746] device (ttyUSB0): state change: prepare -> failed (reason 'gsm-registration-timeout') [40 120 32]
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6751] active-connection[0x219e220]: set state deactivated (was activating)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6752] active-connection[0x219e220]: check-master-ready: not signalling (state deactivated, no master)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6753] device[0x21de800] (ttyUSB0): remove_pending_action (0): 'activation::0x219e220'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6756] (ttyUSB0): notifying ModemManager about the modem disconnection
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6759] policy: connection 'Plus' failed to autoconnect; 3 tries left
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <warn>  [1504257210.6788] device (ttyUSB0): Activation: failed for connection 'Plus'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6790] device[0x21de800] (ttyUSB0): add_pending_action (1): 'queued state change to disconnected'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6791] device[0x21de800] (ttyUSB0): queued state change to disconnected due to none (id 12989)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6841] device[0x21de800] (ttyUSB0): running queued state change to disconnected (id 12989)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <info>  [1504257210.6842] device (ttyUSB0): state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6843] device[0x21de800] (ttyUSB0): deactivating device (reason 'none') [0]
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6844] firewall: [0x2121630,remove*:"ttyUSB0"]: firewall zone remove ttyUSB0:default (not running, simulate success)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6845] firewall: [0x2121630,remove*:"ttyUSB0"]: complete: drop request simulating success
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6846] device[0x21de800] (ttyUSB0): remove_pending_action (1): 'dhcp6' not pending (expected)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6846] device[0x21de800] (ttyUSB0): remove_pending_action (1): 'autoconf6' not pending (expected)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6848] platform-linux: sysctl: failed to open '/proc/sys/net/ipv6/conf/ttyUSB0/accept_ra': (2) Nie ma takiego pliku ani katalogu
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6861] platform-linux: sysctl: failed to open '/proc/sys/net/ipv6/conf/ttyUSB0/use_tempaddr': (2) Nie ma takiego pliku ani katalogu
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6863] (ttyUSB0): notifying ModemManager about the modem disconnection
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6868] device[0x21de800] (ttyUSB0): ip4-config: update (commit=1, routes-full-sync=1, new-config=(nil))
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6869] device[0x21de800] (ttyUSB0): ip6-config: update (commit=1, routes-full-sync=1, new-config=(nil))
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6879] dns-mgr: (update_routing_and_dns): queueing DNS updates (1)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6881] dns-mgr: (update_routing_and_dns): DNS configuration did not change
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6882] dns-mgr: (update_routing_and_dns): no DNS changes to commit (0)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6882] device[0x21de800] (ttyUSB0): add_pending_action (2): 'autoactivate'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6884] active-connection[0x219e220]: disposing
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6894] device[0x21de800] (ttyUSB0): remove_pending_action (1): 'queued state change to disconnected'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <info>  [1504257210.6947] policy: auto-activating connection 'Plus'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6964] active-connection[0x219e340]: set device "ttyUSB0" [0x21de800]
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6965] device[0x21de800] (ttyUSB0): add_pending_action (2): 'activation::0x219e340'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6966] active-connection[0x219e340]: constructed (NMActRequest, version-id 19)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6967] device[0x21de800] (ttyUSB0): remove_pending_action (1): 'autoactivate'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <info>  [1504257210.6981] device (ttyUSB0): Activation: starting connection 'Plus' (4b77e7b1-a7fc-49db-8cb3-7b516041aaf7)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6982] device[0x21de800] (ttyUSB0): activation-stage: schedule activate_stage1_device_prepare,2 (id 13000)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6986] device[0x21de800] (ttyUSB0): activation-stage: invoke activate_stage1_device_prepare,2 (id 13000)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <info>  [1504257210.6986] device (ttyUSB0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6989] active-connection[0x219e340]: set state activating (was unknown)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6990] active-connection[0x219e340]: check-master-ready: not signalling (state activating, no master)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6992] (ttyUSB0): launching connection with ip type 'ipv4' (try 1)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.6995] device[0x21de800] (ttyUSB0): activation-stage: complete activate_stage1_device_prepare,2 (id 13000)
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.7012] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:13:30 ThinkPad-X260 NetworkManager[988]: <debug> [1504257210.7014] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
```

Log when set to configuration 3
```
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5179] active-connection[0x219e460]: set device "cdc-wdm1" [0x212a800]
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5180] device[0x212a800] (cdc-wdm1): add_pending_action (1): 'activation::0x219e460'
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5181] active-connection[0x219e460]: constructed (NMActRequest, version-id 23)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5184] auth: call[75]: CheckAuthorization(org.freedesktop.NetworkManager.network-control), subject=unix-process[pid=1358, uid=1000, start=1355]
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5237] auth: call[75]: CheckAuthorization succeeded: (is_authorized=1, is_challenge=0)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <info>  [1504257494.5262] device (cdc-wdm1): Activation: starting connection 'PlusGSM' (ac811fc1-343f-4e4f-a604-a2fac9836f36)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5263] device[0x212a800] (cdc-wdm1): activation-stage: schedule activate_stage1_device_prepare,2 (id 14111)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <info>  [1504257494.5268] audit: op="connection-activate" uuid="ac811fc1-343f-4e4f-a604-a2fac9836f36" name="PlusGSM" pid=1358 uid=1000 result="success"
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5272] device[0x212a800] (cdc-wdm1): activation-stage: invoke activate_stage1_device_prepare,2 (id 14111)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <info>  [1504257494.5274] device (cdc-wdm1): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5280] active-connection[0x219e460]: set state activating (was unknown)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5281] active-connection[0x219e460]: check-master-ready: not signalling (state activating, no master)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5285] (cdc-wdm1): launching connection with ip type 'ipv4v6' (try 1)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5290] device[0x212a800] (cdc-wdm1): activation-stage: complete activate_stage1_device_prepare,2 (id 14111)
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5308] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:18:14 ThinkPad-X260 NetworkManager[988]: <debug> [1504257494.5318] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect started...
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (4/8): Wait to get fully enabled
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (5/8): Register
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (6/8): Bearer
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (7/8): Connect
Sep  1 11:18:14 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (registered -> connecting)
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (connecting -> registered)
Sep  1 11:18:18 ThinkPad-X260 NetworkManager[988]: <debug> [1504257498.8298] (cdc-wdm1): launching connection with ip type 'ipv4' (try 1)
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect started...
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (4/8): Wait to get fully enabled
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (5/8): Register
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (6/8): Bearer
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (7/8): Connect
Sep  1 11:18:18 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (registered -> connecting)
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (connecting -> registered)
Sep  1 11:18:22 ThinkPad-X260 NetworkManager[988]: <debug> [1504257502.8694] (cdc-wdm1): launching connection with ip type 'ipv6' (try 1)
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect started...
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (4/8): Wait to get fully enabled
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (5/8): Register
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (6/8): Bearer
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Simple connect state (7/8): Connect
Sep  1 11:18:22 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (registered -> connecting)
Sep  1 11:18:23 ThinkPad-X260 ModemManager[5529]: <info>  Modem /org/freedesktop/ModemManager1/Modem/2: state changed (connecting -> registered)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <warn>  [1504257503.3927] (cdc-wdm1): failed to connect modem: Requested service option not subscribed
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3928] unmapped error detected: 'Requested service option not subscribed'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <info>  [1504257503.3928] device (cdc-wdm1): state change: prepare -> failed (reason 'unknown') [40 120 1]
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3932] active-connection[0x219e460]: set state deactivated (was activating)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3933] active-connection[0x219e460]: check-master-ready: not signalling (state deactivated, no master)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3934] device[0x212a800] (cdc-wdm1): remove_pending_action (0): 'activation::0x219e460'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3935] (cdc-wdm1): notifying ModemManager about the modem disconnection
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3938] policy: connection 'PlusGSM' failed to autoconnect; 2 tries left
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <warn>  [1504257503.3943] device (cdc-wdm1): Activation: failed for connection 'PlusGSM'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3944] device[0x212a800] (cdc-wdm1): add_pending_action (1): 'queued state change to disconnected'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3944] device[0x212a800] (cdc-wdm1): queued state change to disconnected due to none (id 14201)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3956] device[0x212a800] (cdc-wdm1): running queued state change to disconnected (id 14201)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <info>  [1504257503.3957] device (cdc-wdm1): state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3957] device[0x212a800] (cdc-wdm1): deactivating device (reason 'none') [0]
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3957] firewall: [0x21f26a0,remove*:"cdc-wdm1"]: firewall zone remove cdc-wdm1:default (not running, simulate success)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3958] firewall: [0x21f26a0,remove*:"cdc-wdm1"]: complete: drop request simulating success
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3958] device[0x212a800] (cdc-wdm1): remove_pending_action (1): 'dhcp6' not pending (expected)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3959] device[0x212a800] (cdc-wdm1): remove_pending_action (1): 'autoconf6' not pending (expected)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3959] platform-linux: sysctl: failed to open '/proc/sys/net/ipv6/conf/cdc-wdm1/accept_ra': (2) Nie ma takiego pliku ani katalogu
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3960] platform-linux: sysctl: failed to open '/proc/sys/net/ipv6/conf/cdc-wdm1/use_tempaddr': (2) Nie ma takiego pliku ani katalogu
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3960] (cdc-wdm1): notifying ModemManager about the modem disconnection
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3962] device[0x212a800] (cdc-wdm1): ip4-config: update (commit=1, routes-full-sync=1, new-config=(nil))
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3963] device[0x212a800] (cdc-wdm1): ip6-config: update (commit=1, routes-full-sync=1, new-config=(nil))
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3967] dns-mgr: (update_routing_and_dns): queueing DNS updates (1)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3968] dns-mgr: (update_routing_and_dns): DNS configuration did not change
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3968] dns-mgr: (update_routing_and_dns): no DNS changes to commit (0)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3969] device[0x212a800] (cdc-wdm1): add_pending_action (2): 'autoactivate'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3970] active-connection[0x219e460]: disposing
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3973] device[0x212a800] (cdc-wdm1): remove_pending_action (1): 'queued state change to disconnected'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <info>  [1504257503.3979] policy: auto-activating connection 'PlusGSM'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3989] active-connection[0x219e340]: set device "cdc-wdm1" [0x212a800]
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3989] device[0x212a800] (cdc-wdm1): add_pending_action (2): 'activation::0x219e340'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3990] active-connection[0x219e340]: constructed (NMActRequest, version-id 24)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.3990] device[0x212a800] (cdc-wdm1): remove_pending_action (1): 'autoactivate'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <info>  [1504257503.4001] device (cdc-wdm1): Activation: starting connection 'PlusGSM' (ac811fc1-343f-4e4f-a604-a2fac9836f36)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4002] device[0x212a800] (cdc-wdm1): activation-stage: schedule activate_stage1_device_prepare,2 (id 14210)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4005] device[0x212a800] (cdc-wdm1): activation-stage: invoke activate_stage1_device_prepare,2 (id 14210)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <info>  [1504257503.4006] device (cdc-wdm1): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4008] active-connection[0x219e340]: set state activating (was unknown)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4008] active-connection[0x219e340]: check-master-ready: not signalling (state activating, no master)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4010] (cdc-wdm1): launching connection with ip type 'ipv4v6' (try 1)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4012] device[0x212a800] (cdc-wdm1): activation-stage: complete activate_stage1_device_prepare,2 (id 14210)
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4018] device[0x211b850] (wlp4s0): add_pending_action (1): 'autoactivate'
Sep  1 11:18:23 ThinkPad-X260 NetworkManager[988]: <debug> [1504257503.4020] device[0x211b850] (wlp4s0): remove_pending_action (0): 'autoactivate'
```


It has somehow connected once by network manager, suddenly durring I was "playing" with wvdial. I could not reproduce in again.
In Widows device is working properly. 
Any ideas? Thanks in advance.

---

### Post by praseodym on 2017-09-02
Please show
```

lsusb
usb-devices
lsmod
```
Is it shown as cable modem in the network manager?

---

### Post by rupert2 on 2017-09-03
```
[FONT=monospace][COLOR=#000000]lsusb[/COLOR]
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 138a:0017 Validity Sensors, Inc. Fingerprint Reader
Bus 001 Device 005: ID 04f2:b52c Chicony Electronics Co., Ltd  
Bus 001 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 001 Device 017: ID 12d1:15c1 Huawei Technologies Co., Ltd.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]usb-devices[/COLOR]

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=12
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.10
S:  Manufacturer=Linux 4.10.0-33-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#= 17 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=ff MxPS=64 #Cfgs=  3
P:  Vendor=12d1 ProdID=15c1 Rev=01.02
S:  Manufacturer=Huawei Technologies Co., Ltd.
S:  Product=HUAWEI Mobile
S:  SerialNumber=0123456789ABCDEF
C:  #Ifs= 3 Cfg#= 3 Atr=a0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0e Prot=00 Driver=cdc_mbim
I:  If#= 1 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=cdc_mbim
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=06 Prot=14 Driver=option

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=058f ProdID=9540 Rev=01.20
S:  Manufacturer=Generic
S:  Product=EMV Smartcard Reader
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=50mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0b(scard) Sub=00 Prot=00 Driver=(none)

T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1                                                                                                                         
P:  Vendor=046d ProdID=c52b Rev=12.01                                                                                                                                                
S:  Manufacturer=Logitech                                                                                                                                                            
S:  Product=USB Receiver                                                                                                                                                             
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA                                                                                                                                                
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid                                                                                                                 
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid                                                                                                                 
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid                                                                                                                 
                                                                                                                                                                                     
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=04 Dev#=  5 Spd=480 MxCh= 0                                                                                                                    
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1                                                                                                                         
P:  Vendor=04f2 ProdID=b52c Rev=00.29                                                                                                                                                
S:  Manufacturer=Chicony Electronics Co.,Ltd.                                                                                                                                        
S:  Product=Integrated Camera                                                                                                                                                        
S:  SerialNumber=0001                                                                                                                                                                
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA                                                                                                                                               
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo                                                                                                               
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo                                                                                                               
                                                                                                                                                                                     
T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=05 Dev#=  6 Spd=12  MxCh= 0                                                                                                                    
D:  Ver= 1.10 Cls=ff(vend.) Sub=11 Prot=ff MxPS= 8 #Cfgs=  1                                                                                                                         
P:  Vendor=138a ProdID=0017 Rev=00.78                                                                                                                                                
S:  SerialNumber=e41ed1b28f47                                                                                                                                                        
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA                                                                                                                                               
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)                                                                                                                 
                                                                                                                                                                                     
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.10
S:  Manufacturer=Linux 4.10.0-33-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]lsmod[/COLOR]
Module                  Size  Used by
mmc_block              36864  2
md4                    16384  0
nls_utf8               16384  2
cifs                  704512  3
ccm                    20480  2
fscache                61440  1 cifs
hid_logitech_hidpp     28672  0
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
bnep                   20480  2
cdc_mbim               16384  0
cdc_wdm                20480  2 cdc_mbim
cdc_ncm                36864  1 cdc_mbim
snd_hda_codec_hdmi     49152  1
binfmt_misc            20480  1
nls_iso8859_1          16384  1
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
option                 53248  0
cdc_ether              16384  0
usb_wwan               20480  1 option
usbnet                 45056  3 cdc_mbim,cdc_ether,cdc_ncm
usbserial              49152  2 option,usb_wwan
mii                    16384  1 usbnet
aesni_intel           167936  4009
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  2005 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
snd_soc_skl            65536  0
videobuf2_memops       16384  1 videobuf2_vmalloc
snd_soc_skl_ipc        49152  1 snd_soc_skl
videobuf2_v4l2         24576  1 uvcvideo
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
iwlmvm                372736  0
snd_hda_codec_realtek    90112  1
rtsx_pci_ms            20480  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_soc_sst_match      16384  1 snd_soc_skl
media                  40960  2 uvcvideo,videodev
mac80211              782336  1 iwlmvm
input_leds             16384  0
memstick               16384  1 rtsx_pci_ms
snd_soc_core          233472  1 snd_soc_skl
snd_compress           20480  1 snd_soc_core
joydev                 20480  0
ac97_bus               16384  1 snd_soc_core
thinkpad_acpi          94208  1
serio_raw              16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_seq_midi           16384  0
iwlwifi               225280  1 iwlmvm
btusb                  45056  0
snd_seq_midi_event     16384  1 snd_seq_midi
btrtl                  16384  1 btusb
nvram                  16384  1 thinkpad_acpi
btbcm                  16384  1 btusb
btintel                16384  1 btusb
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
bluetooth             557056  11 btrtl,btintel,bnep,btbcm,btusb
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_intel          36864  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
mei_me                 40960  0
snd_hwdep              16384  1 snd_hda_codec
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
intel_pch_thermal      16384  0
snd_timer              32768  2 snd_seq,snd_pcm
mei                   102400  1 mei_me
shpchp                 36864  0
snd                    77824  20 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,thinkpad_acpi,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_dev
ice,snd_hda_codec_realtek,snd_soc_core,snd_pcm
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
sunrpc                335872  1
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  3
rtsx_pci_sdmmc         24576  0
i915                 1449984  43
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
sysimgblt              16384  1 drm_kms_helper
e1000e                249856  0
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  14 i915,drm_kms_helper
ahci                   36864  5
ptp                    20480  1 e1000e
pps_core               16384  1 ptp
libahci                32768  1 ahci
wmi                    16384  0
video                  40960  2 thinkpad_acpi,i915
fjes                   77824  0

[/FONT]
```

In Network Manager I can add mobile broadband connection and then chose device. When modem is set to configuration no.2 it is shown as Huawei ME906s, when device is set to configuration no.3 is not seen (I can only chose between "any GSM device" and any CDMA device").
In configuration 2:
```
[FONT=monospace][COLOR=#000000]nmcli dev[/COLOR]
DEVICE      TYPE       STAN                      PO&#321;&#260;CZENIE  
[COLOR=#18B218]wlp4s0[/COLOR][COLOR=#18B218]wifi[/COLOR][COLOR=#18B218]po&#322;&#261;czono[/COLOR][COLOR=#18B218]Ocean15H[/COLOR]
[COLOR=#B26818]ttyUSB0[/COLOR][COLOR=#B26818]gsm[/COLOR][COLOR=#B26818]&#322;&#261;czenie (przygotowanie)[/COLOR][COLOR=#B26818]Plus[/COLOR]
enp0s31f6   ethernet  niedost&#281;pne               --          
lo          loopback  niezarz&#261;dzane             --  
[/FONT]
```

or, in configuration 3:
```
[FONT=monospace][COLOR=#000000] nmcli dev[/COLOR]
DEVICE      TYPE       STAN                      PO&#321;&#260;CZENIE  
[COLOR=#18B218]wlp4s0[/COLOR][COLOR=#18B218]wifi[/COLOR][COLOR=#18B218]po&#322;&#261;czono[/COLOR][COLOR=#18B218]Ocean15H[/COLOR]
[COLOR=#B26818]cdc-wdm0[/COLOR][COLOR=#B26818]gsm[/COLOR][COLOR=#B26818]&#322;&#261;czenie (przygotowanie)[/COLOR][COLOR=#B26818]Plus[/COLOR]
enp0s31f6   ethernet  niedost&#281;pne               --          
lo          loopback  niezarz&#261;dzane             --    
[/FONT]
```

Sorry for polish code, I can translate it if there is such need.
Thanks for answer

---

### Post by rupert2 on 2017-09-13
I make it work!! Not sure what an I doing, but it works.
I found the following scripts:
[HTML]https://github.com/grandcentrix/thinkpad-x260-modem-scripts[/HTML]

follow the instructions, but before building deb package I made changes:
in /usr/local/bin/mbimcli_ip_parser 
change DEV="wwp0s20f0u3i12" into DEV="wwp0s20f0u3c3" (I assume It's my device name)
in /etc/mbim-network.conf
set my APN - in my case it is: "internet"
than build deb and install.

than run lte_start. After that i can connect in Network Manager an it's working.

But there is problem in device name. In script 'lte_start' uses 'cdc-wdm0', but sometimes after resume the device changes to 'cdc-wdm1', so script stops working.

I also wander if it can be integrated with Network Manager by pre-up scripts (/etc/NetworkManager/dispatcher.d/pre-up.d/). I can not find any documentation how to write it - any help?

---

