---
title: "VirtualBox or network interfaces problem? Can't find a solution."
date: 2018-07-11
forum: Networking &amp; Wireless
---

### Post by harardin on 2018-07-11
Hi everyone.

I have installed two systems in VirtualBox one is UbuntuServer 16.04 (planing to use as a host with squid) and a second is Ubuntu 16.04 32-bit (just a client)

InternalNetwork for machines was created with following command:
```
vboxmanage dhcpserver add --netname testlab --ip 10.10.0.1 --netmask 255.255.255.0 --lowerip 10.10.10.1 --upperip 10.10.10.100 --enable
```

**UbuntuServer(host)** network settings in VirtualBox is:
[IMG]https://1.downloader.disk.yandex.ru/preview/710a2ab9bdf58edb3620f73a91013897ea5f21cbb82e9211fee6ddadb89d68c5/inf/ohH8kzBZsJEWUaasgs3eIwnOBr-yJlVZL1kksqWT_WNZ4ekrwVQOJO2MsDURNX86NwkQk13KxKZLzbgu9SGCgA%3D%3D?uid=200209545&filename=HostMachineVB.jpg&disposition=inline&hash=&limit=0&content_type=image%2Fjpeg&tknv=v2&size=1251x549[/IMG]
**Ubuntu 16.04(client)** VirtualBox network settings:
[IMG]https://3.downloader.disk.yandex.ru/preview/741526ea3411f5f107c36278e81cc66e76345b99f22fc57a427c4831bc7fbec4/inf/ohH8kzBZsJEWUaasgs3eI6SudkHByFWG7nn8AW3m0sWJ-gUDpLFSkM1jmQBrq8NEYS8iOAgWZY8kIcV0nwe06A%3D%3D?uid=200209545&filename=ClientMachineVB.jpg&disposition=inline&hash=&limit=0&content_type=image%2Fjpeg&tknv=v2&size=1251x549[/IMG]

**NetworkInterfaces** .conf on **UbuntuServer **looks like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3                    #Connection to the main internet (host machine of VB)
 iface enp0s3 inet dhcp

auto enp0s8                    # Internal network connection
 iface enp0s8 inet dhcp
```

And on the **client** machine everything just stays as it was from default.

Lets get to the **squid **
main config in **http_acces** I have added only this:
```
http_access allow all
```

Here is the things that I also added:
```
forwarded_for off
request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all
```

I want to establish a proxy connection for the **client machine** so the internet see the **client** with it's **IP** that was given buy a **squid** and not the main connection from a provider.

Client machine can ping host but din't get any access to the internet itself.

Here is the input from **ifconfig** on **UbuntuServer(host)**
[IMG]https://2.downloader.disk.yandex.ru/preview/9b169f8b65ff3b369ae641ce9752fbfdba37e00c961a17b6c913c7c115b98888/inf/ohH8kzBZsJEWUaasgs3eI6jyhbdmtI608wrZxSVQTsgaAVbaXymcAUAy7WbZM7ox7Yzc8di-R15k8dOvV0YEGw%3D%3D?uid=200209545&filename=ifConfig.jpg&disposition=inline&hash=&limit=0&content_type=image%2Fjpeg&tknv=v2&size=1251x549[/IMG]


For now I'am stuck please help. I don't ask for a full solution just the direction will be good. Thank you.

---

