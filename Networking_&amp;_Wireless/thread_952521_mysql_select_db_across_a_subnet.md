---
title: "mysql_select_db across a subnet"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by stanleytberry on 2008-10-19
UBUNTU Server v8.04
On a web page:
```
require_once 'frames_includes/navigationDB.inc';
$navigation_connection = mysql_connect($navigation_hostName,
                                       $navigation_userName,
                                       $navigation_passWord) 
  or
die("Failed to connect to MySQL on the nasServer ... call Stan");
mysql_select_db($navigation_databaseName,$navigation_connection) 
  or
die("Selection of 'navigation' database failed ... call Stan");
$navigation_data = mysql_query("SELECT * FROM " .
                        $navigation_databaseName . ".navigate " .
                        "ORDER BY navigateHandle",
                        $navigation_connection)
  or
die("SELECT * FROM navigate table failed ... call Stan");
```
works when the UBUNTU server is attached to the same subnet as the MySQL server.

If I move the UBUNTU server to a different subnet (through an ipCop machine), making appropriate adjustments to network configuration, including punching a hole in the firewall for port 3306 from the UBUNTU server to the MySQL server and authorizing the user at the new IP to MySQL, the mysql_connect works but the **mysql_select_db fails**.

I need help debugging this, please?

Thanks,
Stan

---

