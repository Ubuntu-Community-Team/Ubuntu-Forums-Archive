---
title: "NX not working with new Hardy installation"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Nazrax on 2008-05-26
I've got a fresh Hardy installation. I've installed the newest nxclient, nxnode, and nxserver debs from nomachine.com. Unfortunately, it's not working.

At first, when I tried to use NX, the logs complained that it didn't have permission to create .nx in my home directory. I never had a problem with that before, but I created a .nx directory and set its permissions to 1777. 

I tried again, but it still failed. This time, xauth is having a problem. Here's the complete log entry:

```

May 26 17:33:52 theseus NXSERVER-3.2.0-7[3515]: User 'adrian' logged in from '192.168.0.100'. 'NXLogin::set'
May 26 17:33:56 theseus NXSERVER-3.2.0-7[3515]: Selected node host:localhost with port:22 'main::selectNode'
May 26 17:33:56 theseus NXSERVER-3.2.0-7[3515]: Current selected node: localhost is in status: running  'main::selectNode'
May 26 17:33:56 theseus NXSERVER-3.2.0-7[3515]: Selected session type: unix-desktop allowed in the profile of user: adrian 'NXShell::Static'
May 26 17:33:56 theseus NXSERVER-3.2.0-7[3515]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
May 26 17:33:57 theseus NXSERVER-3.2.0-7[3515]: A valid NX Server public SSH key is missing on the node. '(eval)'
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.2.0-5  (Error id e4C836D) [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 ERROR: create session: run commands [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 ERROR: execution of last command failed [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/adrian/.nx/C-theseus-1004-5E4D4C03D43B53398B273EC4207FBBAC/scripts/authority' [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 exit value: 1 [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 stdout:  [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 stderr: xauth:  timeout in locking authority file /home/adrian/.Xauthority [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 . [e4C836D] Logger::log nxnode 2833
May 26 17:34:19 theseus NXNODE-3.2.0-5[3542]: ERROR: NX> 596 init: stdin arguments: user=adrian,userip=192%2e168%2e0%2e100,uniqueid=5E4D4C03D43B53398B273EC4207FBBAC,display=1004,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e10,encryption_mode=3,connection=local,images=64M,cache=16M,client=linux,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,rootless=1,shpix=1,composite=1,application=k3b,session=theseus%2dk3b,shmem=1,type=unix%2ddesktop,virtualdesktop=1,screeninfo=1440x848x24%2brender,keyboard=pc105%2fus,link=lan Logger::log nxnode 2833
May 26 17:34:20 theseus NXNODE-3.2.0-5[3542]: getting agent pid: cannot read pid file '/home/adrian/.nx/C-theseus-1004-5E4D4C03D43B53398B273EC4207FBBAC/pids/agent'. Exiting. main::get_agent_pid nxnode 8655
May 26 17:34:20 theseus NXNODE-3.2.0-5[3542]: directory '/home/adrian/.nx/C-theseus-1004-5E4D4C03D43B53398B273EC4207FBBAC' moved into '/home/adrian/.nx/F-C-theseus-1004-5E4D4C03D43B53398B273EC4207FBBAC' for investigation Logger::log nxnode 8712

```

I set .Xauthority's permissions to 666 (horrible, I know - I'm trying everything right now) and it's still giving me the same error.

This was never this hard before. What's going on? How do I fix this?

Thank you.

---

