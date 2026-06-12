---
title: "Netplan error"
date: 2021-09-12
forum: Networking &amp; Wireless
---

### Post by bomberb17 on 2021-09-12
I am running Ubuntu server 20.04.3 LTS on a remote Raspberry Pi 4.
It is connected through WiFi to a remote router (IP 192.168.1.1), and I had configured networking with netplan.
However after some months I decided to change the DNS configuration, i.e. remove my router local DNS and replace it with Cloudflare's DNS.
So knowing that the yaml file is very sensitive with spaces, the only change I made is to remove the "92" and "68", so the file now is as follows:

```
$ cat /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            dhcp4: true
    wifis:
        wlan0:
            dhcp4: no
            addresses: [192.168.1.12/24]
            gateway4: 192.168.1.1
            nameservers:
                addresses: [1.1.1.1, 8.8.8.8]
            access-points:
                "accesspointname":
                    password: "accesspointpassword"
    version: 2
```


However when I run netplan try, I get the following:

```
$ sudo netplan try
Job for netplan-wpa-wlan0.service canceled.

An error occurred: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.

Reverting.
Warning: Stopping systemd-networkd.service, but it can still be activated by:
  systemd-networkd.socket
```

or

```
$ sudo netplan try
Job for netplan-wpa-wlan0.service canceled.

An error occurred: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.

Reverting.
Job for netplan-wpa-wlan0.service canceled.
Traceback (most recent call last):
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 84, in command_try
    NetplanApply().command_apply(run_generate=True, sync=True, exit_on_error=False)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 164, in command_apply
    utils.systemctl_networkd('stop', sync=sync, extra_services=wpa_services)
  File "/usr/share/netplan/netplan/cli/utils.py", line 131, in systemctl_networkd
    subprocess.check_call(command)
  File "/usr/lib/python3.8/subprocess.py", line 364, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/sbin/netplan", line 23, in <module>
    netplan.main()
  File "/usr/share/netplan/netplan/cli/core.py", line 50, in main
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 264, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 66, in run
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 264, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 95, in command_try
    self.revert()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 118, in revert
    NetplanApply().command_apply(run_generate=False, sync=True, exit_on_error=False)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 164, in command_apply
    utils.systemctl_networkd('stop', sync=sync, extra_services=wpa_services)
  File "/usr/share/netplan/netplan/cli/utils.py", line 131, in systemctl_networkd
    subprocess.check_call(command)
  File "/usr/lib/python3.8/subprocess.py", line 364, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.
```



I want to be very careful with this as I don't want to break networking, as I don't have local access to fix things if needed. Also I'm not sure if I reboot the system if it will lose connection!
Any suggestions?

---

