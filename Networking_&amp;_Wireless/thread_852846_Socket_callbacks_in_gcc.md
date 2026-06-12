---
title: "Socket callbacks in gcc?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by torigo on 2008-07-08
In Windows I can register for callbacks for events such as network address list change or routing table change:

WSAIoctl(mySocket, SIO_ADDRESS_LIST_CHANGE, NULL, 0, NULL, 0, & addrSize, pol, myCallback);

If my address list changes the system will call my function. I can't find anything comparable in gcc/Linux! Do I really have to poll to find out if my address list or route table has changed?

Thanks -

---

