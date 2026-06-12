---
title: "Is network-admin working properly?"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by Angel Herranz on 2005-10-22
Sometimes network-admin does not save the configuration correctly.

I run it from a terminal and it broke with a message about an assertion violation (something that had to do with a NULL value returned by gst_xml_current_element).

has anyone noticed problems?

PS. I posted a pair of messages in the Ubuntu desktop forum but none answered :(

---

### Post by Angel Herranz on 2005-10-23
Here is the message:

```

angel@exodo4:~$ network-admin

** (network-admin:8000): CRITICAL **: gst_xml_element_set_content: assertion `node != NULL' failed

** (network-admin:8000): CRITICAL **: gst_xml_element_set_content: assertion `node != NULL' failed

```

---

### Post by joshuapurcell on 2005-11-21
This happens to me almost every time I use network-admin. I use it on a daily basis to switch from DHCP to static when needed, and I haven't found any functionality problems in relation to this error message yet. It would be nice to know what it means though.

---

