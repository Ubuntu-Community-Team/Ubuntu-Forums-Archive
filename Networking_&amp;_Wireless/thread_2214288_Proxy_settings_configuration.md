---
title: "Proxy settings configuration ?"
date: 2014-03-31
forum: Networking &amp; Wireless
---

### Post by hansokl on 2014-03-31
Hi,

I have a VM running 8.04.4 LTS and can't seem to access the internet. I am first trying to run apt-get update and upgrade but I get messages that it failed to fetch url/file then 404 Not Found.

What I have done:

ran the commands

export http_proxy=http://Proxy server:port#
export https_proxy=http://Proxy server:port#
export ftp_proxy=http://Proxy server:port#

I also created the file apt.conf (since it didn't exist) and placed the following in the file:

Aquire::http:: Proxy "http://proxy server:port#";
Aquire::ftp::Proxy "http://proxy server:port#";


I'm not sure if I have to edit another file or not. I've done some searching before posting here for help. Anyone have an idea of what my issue is? Thanks!

(side note - The proxy server is working correctly for other VMs that are running 12.04 LTS)

---

### Post by bapoumba on 2014-03-31
[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)
This is how I use it. The apt.conf file used to be enough for me on Hardy. Why are you still on 8.04 ? I admit Hardy has been my favorite for a long time, but that was a long time ago. Hardy server has reached end of life last July. No more updates, even security updates.

Edit : EOL was in May 2013, not July.

---

