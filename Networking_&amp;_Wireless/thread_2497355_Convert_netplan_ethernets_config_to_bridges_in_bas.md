---
title: "Convert netplan ethernets config to bridges in bash script"
date: 2024-05-02
forum: Networking &amp; Wireless
---

### Post by bradley-coder7 on 2024-05-02
Hello all. I'm working on a script that will need to convert an existing, straightforward netplan config with an ethernets section into a bridged config. This is so that the script can build bridged connections for KVM instances. I've come up with a way that should work, but I'm wondering if there is a better way.

Proof of concept using echo (the real one would edit the config file in-place):

```
IFNAME=$(ip route get 1.1.1.1 | grep -oP "(?<=dev )([^ ]*)")
echo "network:
    ethernets:
        enp3s0:
            addresses:
            - 192.168.1.16/24
            dhcp6: true
            nameservers:
                addresses:
                - 1.1.1.1
                - 1.0.0.1
                search:
                - example.com
            routes:
            -   to: default
                via: 192.168.1.254
    version: 2
"|
yq -y "{\"interfaces\": [\"$IFNAME\"] } as \$ifs | 
{\"br0\":.network.ethernets.$IFNAME } as \$br | 
{\"bridges\": \$br} as \$brs | 
{\"$IFNAME\": {}} as \$nif | 
del(.network.ethernets.$IFNAME) | 
.network.ethernets += \$nif | 
.network += \$brs | 
.network.bridges.br0 += \$ifs"
```

Does anyone have a better way of doing this from bash?

The target environment is an Ubuntu Server 24.04 default install.

---

### Post by TheFu on 2024-05-04
I would slurp the specific data from the file, place that into variables, then simply print the desired config out in the required YAML format. bash could do it with an remote ssh push function to get the script on each remote system to be run.
```
  ssh $RUSER@$REMOTE 'bash -s' <<ENDSSH
    # ################################################
    function LogItDebug()
    {
       if [ $DEBUG = 1 ] ; then
         echo "DEBUG: $BASH_SOURCE @ $BASH_LINENO in $FUNCNAME"
       fi
    }
ENDSSH

```Add as many bash functions as you like inside that, then call them as desired.  I cut that from one of my backup scripts, removing about 20 functions that are used to gather information before the code pulls backups to a central server.  

Or you could use a tool like Ansible, have it gather facts, then use the netplan YAML module to generate the output.    Ansible has all sorts of uses.
[https://github.com/mrlesmithjr/ansible-netplan](https://github.com/mrlesmithjr/ansible-netplan)  BTW, facts are gathered automatically, just running ansible, so generating a template and filling in the existing values, then removing the old file would be fairly trivial AND reusable.  There must be over 1000 items of "facts" that Ansible puts into variables as part of each run. These variables can be used to modify or fill in values for any number of config files.   Ansible is pretty easy and most Linux distros meet the pre-requisites required for ansible connections to be used.  Just need a deployment account with ssh and sudo on each remote system.  Best not to use root or a personal user for obvious reasons.

It comes down to whether you want a 1-off script to manage forever or want to re-use tools that 100K+ admins are using today.

The number of systems impacted and how long this script will need to be used would go into the question for how much effort should be expended.  If this is for less than 1000 uses and you have a solution that works, I wouldn't think about it any more.
If you already have a devops tool for all the systems, I'd look for how that tool does things like this.

As usual, for small needs (less than 1000 systems), whatever works is the best answer.  Don't over-complicate it.  I'd use perl if the bash got too long, but the more I think about it, ansible would be better long term.

Oh - one last thing. I wouldn't edit the file in-place.  I'd move it to a .yaml.bak file so it won't be picked up and create a new YAML file named for the goal of the file.  Something like "br0-static-ip-lan-ns.yaml".  Be certain to set the permissions, owner, group as required (24.04 mandates 600 root:root now) and don't forget to run netplan generate and apply.  Ansible can do all that and will see the return codes, so if there are any issues, you'll be told.

---

