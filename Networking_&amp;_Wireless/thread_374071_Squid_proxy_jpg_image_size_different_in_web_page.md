---
title: "Squid proxy jpg image size different in web page"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by matthey on 2007-03-02
I installed the squid proxy server on Ubuntu 6.06 LTS. I just change the squid.conf file network part, and other keeps unchange. I can visit the Internet web site without any networking connection problem. But I find the image quality is poor.

I saw the image (which is jpeg file) in the web page is poor, and the size is smaller than the orginal.

For example

I visit a web site with squid proxy, I check one image file size "1910 bytes". And then,
I check with another machine (same hardware and software configuration) which direct connect the Internet. I check the same image again. The image quality is better, the file size is "4456 bytes"

I run test many times, and close the browser and clear the browser cache every time before I test. But the result is same. I also visit different web sites, the squid proxy gives poor image cases also happened.

How I solve the problem? Or it is normal case at squid. Thanks

Matthew Yuan

**Sample is included**
The left is image capture from direct connect PC
The right is image capture from proxy connect PC

Here is the testing machine configurations.

Client machine
OS: Windows 2000 with SP4
Browser: Internet Explorer 6.0 SP1

Server machine
OS: Ubuntu 6.06 LTS (already updated)
RAM: 2G RAM
HD: 250GB
Proxy: Squid 2.5

---

