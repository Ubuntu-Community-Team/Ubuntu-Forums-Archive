---
title: "Need help with redirecting qbittorrent-nox webUI"
date: 2019-07-30
forum: Networking &amp; Wireless
---

### Post by login721 on 2019-07-30
In my college network, they block all access except HTTP/https that make me unable to access my home server via ssh or vpn. So I installed shellinabox in my home server and use apache <Location /shell> to redirect to the shellinabox server listening on port 8022. I do the same thing with qbittorrent-nox(<Location /torrent>, server on port 28080), but only the redirect of shellinabox work. With qbittorrent, I can load the webUI page, but it only displays text. 
Can you guy help me what wrong with my qbittorrent config, please! 
Thanks in advance! 
Sorry for my bad English!


/etc/apache2/sites-available/torrent.conf
```
<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin webmaster@localhost
        ServerName mynoipaddr.ddns.net/torrent
        ErrorLog ${APACHE_LOG_DIR}/torrent-error.log
        CustomLog ${APACHE_LOG_DIR}/torrent-access.log combined
        SSLEngine on
        SSLProxyEngine on
        SSLCertificateFile    /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>
    </VirtualHost>
    <Location /torrent>
        ProxyPass http://localhost:28080
        Order allow,deny
        Allow from all
    </Location>
    Redirect permanent /torrent http://192.168.1.102:28080
</IfModule>
```

/var/log/torrent-error.log
```
[Tue Jul 30 20:14:25.579196 2019] [ssl:warn] [pid 9793:tid 140178661270656] AH01906: mynoipaddr.ddns.net/torrent:443:0 server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Jul 30 20:14:25.579321 2019] [ssl:warn] [pid 9793:tid 140178661270656] AH01909: mynoipaddr.ddns.net/torrent:443:0 server certificate does NOT include an ID which matches the server name
[Tue Jul 30 20:14:25.597545 2019] [ssl:warn] [pid 9795:tid 140178661270656] AH01906: mynoipaddr.ddns.net/torrent:443:0 server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue Jul 30 20:14:25.597581 2019] [ssl:warn] [pid 9795:tid 140178661270656] AH01909: mynoipaddr.ddns.net/torrent:443:0 server certificate does NOT include an ID which matches the server name

```

And the console log of firefox
```
.
.
The script from “https://mynoipaddr.ddns.net/scripts/misc.js?locale=en” was loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type. torrent
The script from “https://mynoipaddr.ddns.net/scripts/lib/mootools-1.2-core-yc.js” was loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type. torrent
Loading failed for the <script> with source “https://mynoipaddr.ddns.net/scripts/lib/mootools-1.2-core-yc.js”. torrent:16:1
The script from “https://mynoipaddr.ddns.net/scripts/lib/mootools-1.2-more.js” was loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type. torrent
Loading failed for the <script> with source “https://mynoipaddr.ddns.net/scripts/lib/mootools-1.2-more.js”. torrent:17:1
The script from “https://mynoipaddr.ddns.net/scripts/lib/mocha-yc.js” was loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type. torrent
Loading failed for the <script> with source “https://mynoipaddr.ddns.net/scripts/lib/mocha-yc.js”. torrent:21:1
The script from “https://mynoipaddr.ddns.net/scripts/mocha-init.js?locale=en” was loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type. torrent
.
.
Content Security Policy: The page’s settings blocked the loading of a resource at data:application/font-woff2;charset=utf-… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:application/font-woff;charset=utf-8… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:font/woff;base64,d09GRgABAAAAAJAgAB… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:font/woff;base64,d09GRgABAAAAAI7sAB… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:application/font-woff2;charset=utf-… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:application/font-woff;charset=utf-8… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:font/woff;base64,d09GRgABAAAAAJAgAB… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:font/woff;base64,d09GRgABAAAAAI7sAB… (“default-src”).
Content Security Policy: The page’s settings blocked the loading of a resource at data:font/woff;base64,d09GRgABAAAAAIw4AB… (“default-src”)
.
.
```

---

