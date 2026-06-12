---
title: "dial up connection using bsnl modem"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by pkumar742589 on 2013-10-27
please tell me how to configure pppoe or dial up connection in ubuntu 11.10 using dial up connection

---

### Post by varunendra on 2013-10-27
Welcome to Ubuntu Forums PKumar ! :)

The recommended way to configure PPPoE in Ubuntu is -

Click **Network Manager**'s icon in the top-right corner > "**Edit Connections.." > "DSL" tab > "Add" button > type in the "User Name", "Service" and "Password" correctly > Save and close** the box leaving the rest of the settings at default.

Optionally, you can check the "Connect Automatically" checkbox to let it connect automatically as soon as a cable connection is detected.

Let me know if you need more help on this.

**PS:**
If you have an unlimited connection, or the system is going to be the only system using the modem, it is recommended to configure PPPoE in the modem itself. That is quite straightforward and works flawlessly. It connects automatically as soon as the modem is powered on, and the devices connected to it get the "Ready to use" connection.

---

