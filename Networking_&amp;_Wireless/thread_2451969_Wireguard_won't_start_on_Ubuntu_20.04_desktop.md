---
title: "Wireguard won't start on Ubuntu 20.04 desktop"
date: 2020-10-13
forum: Networking &amp; Wireless
---

### Post by mdwalsh20 on 2020-10-13
Hi,


I have installed Wireguard on Ubuntu 20.04 Desktop.


I used this tutorial URL: [https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/](https://www.cyberciti.biz/faq/ubuntu-20-04-set-up-wireguard-vpn-server/) along with several others that are pretty much the same.


The problem I am experiencing Wireguard won't start.


Here is the error message.


name@name:~$ sudo systemctl start wg-quick@wg0
[sudo] password for name: 
Job for [email]wg-quick@wg0.servic[/email]e failed because the control process exited with error code.
See "systemctl status [email]wg-quick@wg0.servic[/email]e" and "journalctl -xe" for details.


name@name:~$ journalctl -xe
-- Subject: Unit process exited
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- An ExecStart= process belonging to unit [email]wg-quick@wg0.servic[/email]e has exited.
-- 
-- The process' exit code is 'exited' and its exit status is 127.
Oct 13 21:03:36 name-GA-78LMT-S2 systemd[1]: [email]wg-quick@wg0.servic[/email]e: Failed with result 'exit-code'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- The unit [email]wg-quick@wg0.servic[/email]e has entered the 'failed' state with result 'exit-code'.
Oct 13 21:03:36 name-GA-78LMT-S2 systemd[1]: Failed to start WireGuard via wg-quick(8) for wg0.
-- Subject: A start job for unit [email]wg-quick@wg0.servic[/email]e has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- A start job for unit [email]wg-quick@wg0.servic[/email]e has finished with a failure.
-- 
-- The job identifier is 3614 and the job result is failed.
Oct 13 21:03:36 walshm-GA-78LMT-S2 sudo[11889]: pam_unix(sudo:session): session closed for user root
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 13 21:03:39 walshm-GA-78LMT-S2 systemd-resolved[733]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.


[1]+  Stopped                 journalctl -xe


name@name:~$ systemctl status [email]wg-quick@wg0.servic[/email]e
&#9679; [email]wg-quick@wg0.servic[/email]e - WireGuard via wg-quick(8) for wg0
     Loaded: loaded (/lib/systemd/system/wg-quick@.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2020-10-13 21:03:36 CDT; 1min 24s ago
       Docs: man:wg-quick(8)
             man:wg(8)
             [https://www.wireguard.com/](https://www.wireguard.com/)
             [https://www.wireguard.com/quickstart/](https://www.wireguard.com/quickstart/)
             [https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8](https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8)
             [https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8](https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8)
    Process: 11895 ExecStart=/usr/bin/wg-quick up wg0 (code=exited, status=127)
   Main PID: 11895 (code=exited, status=127)


Oct 13 21:03:35 name-GA-78LMT-S2 wg-quick[11895]: [#] ip link add wg0 type wireguard
Oct 13 21:03:35 name-GA-78LMT-S2 wg-quick[11895]: [#] wg setconf wg0 /dev/fd/63
Oct 13 21:03:35 name-GA-78LMT-S2 wg-quick[11895]: [#] ip -4 address add 10.0.0.2/24 dev wg0
Oct 13 21:03:36 name-GA-78LMT-S2 wg-quick[11895]: [#] ip link set mtu 1420 up dev wg0
Oct 13 21:03:36 name-GA-78LMT-S2 wg-quick[11933]: [#] resolvconf -a wg0 -m 0 -x
Oct 13 21:03:36 name-GA-78LMT-S2 wg-quick[11935]: /usr/bin/wg-quick: line 32: resolvconf: command not found
Oct 13 21:03:36 name-GA-78LMT-S2 wg-quick[11895]: [#] ip link delete dev wg0
Oct 13 21:03:36 name-GA-78LMT-S2 systemd[1]: [email]wg-quick@wg0.servic[/email]e: Main process exited, code=exited, status=127/n/a
Oct 13 21:03:36 name-GA-78LMT-S2 systemd[1]: [email]wg-quick@wg0.servic[/email]e: Failed with result 'exit-code'.
Oct 13 21:03:36 name-GA-78LMT-S2 systemd[1]: Failed to start WireGuard via wg-quick(8) for wg0.


Can some suggest how to resolve Wireguard not starting?

---

