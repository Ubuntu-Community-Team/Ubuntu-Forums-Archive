---
title: "Moblock help please"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by AnonUK on 2008-12-02
* Error 7: Missing file /etc/moblock/guarding.p2p.
 * Check the BLOCKLIST setting.
 * BLOCKLIST is set in /etc/moblock/moblock.conf.

I've installed it but as you can see there's a problem^

this is my show_config

root@anonymous-laptop:~# moblock-control show_config
moblock-control current settings:
BLOCKLIST_FORMAT="p"
LOG_TIMESTAMP="0"
LOG_SYSLOG="0"
LOG_IPTABLES=""
VERBOSITY="1"
MOBLOCK_INIT="1"
MOBLOCK_CRON="1"
IPTABLES_TARGET="NFQUEUE"
NFQUEUE_NUMBER="92"
IPTABLES_SETTINGS="1"
IPTABLES_ACTIVATION="1"
REJECT="1"
REJECT_MARK="10"
REJECT_IN="DROP"
REJECT_OUT="REJECT"
REJECT_FW="DROP"
ACCEPT="1"
ACCEPT_MARK="20"
IPTABLES_TARGET_WHITELISTING="RETURN"
WHITE_LOCAL="1"
WHITE_TCP_IN=""
WHITE_UDP_IN=""
WHITE_TCP_OUT="http https"
WHITE_UDP_OUT=""
WHITE_TCP_FORWARD=""
WHITE_UDP_FORWARD=""
WHITE_IP_IN=""
WHITE_IP_OUT=""
WHITE_IP_FORWARD=""
IP_REMOVE=""
PATH="/sbin:/bin:/usr/sbin:/usr/bin"
NAME="moblock"
DAEMON="/usr/bin/moblock"
CONTROL_SCRIPT="/usr/bin/moblock-control"
CONF_DIR="/etc/moblock"
CONTROL_DEFAULT="/etc/default/moblock"
MASTER_BLOCKLIST_DIR="/etc/moblock"
BLOCKLISTS_DIR="/var/spool/moblock"
BLOCKLISTS_DIR_USED="/var/spool/moblock/used"
BLOCKLISTS_LIST="/etc/moblock/blocklists.list"
ALLOW_IN="/etc/moblock/allow.p2p"
ALLOW_OUT="/etc/moblock/allow.p2p"
ALLOW_FW="/etc/moblock/allow.p2p"
IPTABLES_CUSTOM_INSERT="/etc/moblock/iptables-custom-insert.sh"
IPTABLES_CUSTOM_DELETE="/etc/moblock/iptables-custom-remove.sh"
LOG_DIR="/var/log"
DAEMON_LOG="/var/log/moblock.log"
CONTROL_LOG="/var/log/moblock-control.log"
STATFILE="/var/log/MoBlock.stats"
PIDFILE="/var/run/moblock.pid"
LSB="/lib/lsb/init-functions"
TESTHOST="www.bluetack.co.uk"
LSB_MODE="0"

Thanks for any help. i'm not really sure how to fix it :S

---

### Post by AnonUK on 2008-12-02
Oh and also

Updating level1.gz * . No update available.
Updating level2.gzcp: cannot stat `level2.gz': No such file or directory

edit:

I changed the relevant stuff to this:

$ gedit /etc/moblock/moblock.conf (as root)


WHITE_TCP_IN=&#8221;"
WHITE_UDP_IN=&#8221;"
WHITE_TCP_OUT=&#8221;"
# This is an example to whitelist outgoing web traffic (port 80 is the service
# http, 443 is https) and the port range 1000-1024:
#WHITE_TCP_OUT=&#8221;80 443 1000:1024&#8243; #Uncomment this line
WHITE_UDP_OUT=&#8221;"
WHITE_TCP_FORWARD=&#8221;"
WHITE_UDP_FORWARD=&#8221;"

---

### Post by AnonUK on 2008-12-02
root@anonymous-laptop:~# moblock-control update
/etc/moblock/moblock.conf: 157: _: not found
 * Updating blocklists and reloading MoBlock moblock

---

### Post by AnonUK on 2008-12-03
root@anonymous-laptop:~# sudo dpkg-reconfigure moblock-control
/etc/moblock/moblock.conf: 157: _: not found
/etc/moblock/moblock.conf: 157: _: not found
/etc/moblock/moblock.conf: 157: _: not found
/etc/moblock/moblock.conf: 157: _: not found
Error: Failed to source /etc/moblock/moblock.conf although this file exists.
root@anonymous-laptop:~#

---

### Post by bumanie on 2008-12-03
Have a look at [ipblock]("http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html") it is much easier to configure than moblock and uses much the same block lists.

---

### Post by AnonUK on 2008-12-03
> **bumanie said:**
> Have a look at [ipblock]("http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html") it is much easier to configure than moblock and uses much the same block lists.

hi thanks

root@anonymous-laptop:~# sudo dpkg -i iplist_0.14-0feisty1_i386.deb
dpkg: regarding iplist_0.14-0feisty1_i386.deb containing iplist:
 moblock-control conflicts with iplist


should i Purge moblock ? or just remove

---

### Post by uljanow on 2008-12-03
I'd purge both, moblock and iplist version 0.14. Check out this [Howto]("http://ubuntuforums.org/showthread.php?t=530183") to get the latest version.

---

### Post by jre on 2008-12-04
I answered in your thread at phoenixlabs:
[http://forums.phoenixlabs.org/showthread.php?p=120896](http://forums.phoenixlabs.org/showthread.php?p=120896)

Seems as if you broke your moblock.conf ...

Further there are problems with the bluetack lists currently.

But uljanow is right: Whatever application you use, first **purge** all your previous tries.

---

