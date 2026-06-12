---
title: "fsockopen cannot reach my server"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by rocksoccer on 2008-05-30
The ubuntu server 7.10 runs behind a router with a port mapping using port 25011. I can access the website hosted on the server from outside the router. I have another hosting space where I place the main page of the website. Visitors go to the main page first, where php script fsockopen determines the first server status and redirects accordingly.

I have tested the pingDomain function (below), and it works fine to reach sites like google.com or yahoo.com

But, I cannot reach the first server. Forget to mention that I test port check with [http://www.canyouseeme.org/](http://www.canyouseeme.org/), it says port 25011 is reachable.

[PHP]<?php

// Function to check response time
function pingDomain($domain){
    $file = fsockopen ($domain, 25011, $errno, $errstr, 8);
    
    echo $errno;
    echo $errstr;
    $status = 0;

    if (!$file) $status = -1;  // Site is down
    else {
			$status = 1;
			fclose($file);
    }
    return $status;
}
?>[/PHP]

I dont know what is the problem. Is it the problem of ubuntu server configuration or PHP?

Please help. Thanks in advance:confused:

---

