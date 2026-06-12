---
title: "Syslog full of NetworkManager logs"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by michelem09 on 2007-09-06
I have my syslog full of NetworkManager issues, NM seems to work fine but it logs this strings every 5 seconds:

Sep  6 09:45:37 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:45:43 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:45:43 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:45:48 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:45:48 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:45:53 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:45:53 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:45:58 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:45:58 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:04 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:04 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:09 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:09 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:14 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:14 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:19 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:19 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:25 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:25 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:30 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:30 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!! 
Sep  6 09:46:35 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Sep  6 09:46:35 goa NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!!

---

