---
title: "WiFi just vanished"
date: 2021-01-08
forum: Networking &amp; Wireless
---

### Post by timswait on 2021-01-08
The WiFi on my Dell Precision laptop just stopped working this morning. It was fine last night when I shut the machine down, I didn't install any updates yesterday, but this morning Ubuntu is not seeing any WiFi card at all. It's Ubuntu 20.04. The WiFi network is up, other devices are connected to it fine. The Settings>Network menu is showing options for wired network and VPN but does not list anything about WiFi. I can connect by an ethernet cable so at least I'm able to install software to fix it. The output of lspci includes the line:
```
03:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```
The Additional Drivers GUI lists "Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless Network Adapter (Inspiron M5010 / XPS 8300) This device is using an alternative driver"
And the box is checked for "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)"
So it's seeing the Broadcom adapter, why isn't it showing WiFi options in the menu? I have tried turning the 'Airplane Mode' switch on and off. This turns the Bluetooth (which is working fine) on and off as expected but has no effect on the WiFi.

---

### Post by imlee123 on 2021-01-08
My friend is having the same problem. We are trying to fix. See this:

[https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic](https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic)

---

### Post by paul_wilson2 on 2021-01-08
For transparency, I also posted this on the "bcmwl kicked the bucket after kernel update" thread and will not be cross posting further.

The make log (/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log) list the following error.

/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:3376:58: error: passing argument 4 of &#8216;proc_create_data&#8217; from incomp
atible pointer type [-Werror=incompatible-pointer-types]
 3376 |  if ((wl->proc_entry = proc_create_data(tmp, 0644, NULL, &wl_fops, wl)) == NULL) {
      |                                                          ^~~~~~~~
      |                                                          |
      |                                                          const struct file_operations *
In file included from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:38:
./include/linux/proc_fs.h:102:31: note: expected &#8216;const struct proc_ops *&#8217; but argument is of type &#8216;const struct file_operations *&#8217;
  102 | extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
      |                               ^~~~~~~~~~~~~~~~

Looking at /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c the structure file_operations is being used.

In the previous linux 5.4.0-59 header file ./include/linux/proc_fs.h the structure file_operations is being used.

However, in the new kernel 5.8.0-34 header file ./include/linux/proc_fs.h a new structure named proc_ops is now being used.

I am not sure if the fix needs to be on the bcmwl side or on the linux kernal header files side.

I believe this is getting pretty close to the heart of the matter.  Unfortunately, I think it is a matter of waiting for a fix.

---

### Post by timswait on 2021-01-13
> **imlee123 said:**
> My friend is having the same problem. We are trying to fix. See this:

[https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic](https://askubuntu.com/questions/1305699/bcmwl-kernel-source-broken-on-kernel-5-8-0-34-generic)

Thank you, I used the first solution given there (downloading and installing the package from: [http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu7_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu7_amd64.deb)) and it has worked for me.

---

