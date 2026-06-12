---
title: "upload and download bandwidth test in text based (server) environment"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by leonv12 on 2007-12-26
I have several remote ubuntu servers (6.06.10) on which I need to occasionally see what the upload and dowmload bandwidths are.  I have installed lynx, but I can't get it to work with any of the bandwidth web sites that I am familiar with.  

Can anyone help me find a way to check upload and download bandwidth on an ubuntu server?

Thanks in advance,
Leon

---

### Post by santosh_gr on 2007-12-27
If you just want to monitor the software for 1 servers then, you can install software called "bandwidthd" which creates html graphs to show utilisation.

You can host it on a simple web server like "webfs" and monitor it.  It takes only 5 mins to install.  Here are the steps.

apt-get install bandwidthd
apt-get install webfs

you may need to modify /etc/bandwidthd/bandwidthd.conf file to set the subnet mask like

subnet 192.168.0.0/24

you may need to modify /etc/webfsd.conf file to set other parameters e.g.

# The default location of web_root is /var/lib/bandwidthd/htdocs/
web_root=/var/lib/bandwidthd/htdocs/
web_host=
web_ip=
web_port=80
web_virtual=false
web_timeout=
web_conn=
web_index=
web_dircache=
web_accesslog=
web_syslog=false
web_user=www-data
web_group=www-data

Restart 2 services 

/etc/init.d/bandwidthd restart
/etc/init.d/webfs restart

From a different computer you can access the graphs by typing

http://<ip-address>/index.html

---

### Post by leonv12 on 2007-12-27
Thanks,

I will give this a try.

Leon

---

