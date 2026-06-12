---
title: "openvpn ubuntu no internet access from windows client"
date: 2016-06-21
forum: Networking &amp; Wireless
---

### Post by alex422 on 2016-06-21
Having trouble getting access to the internet as well as the local domain file shares on the openvpn server


here are my config files


****server conf file****


    ```
#################################################
    # Sample OpenVPN 2.0 config file for            #
    # multi-client server.                          #
    #                                               #
    # This file is for the server side              #
    # of a many-clients <-> one-server              #
    # OpenVPN configuration.                        #
    #                                               #
    # OpenVPN also supports                         #
    # single-machine <-> single-machine             #
    # configurations (See the Examples page         #
    # on the web site for more info).               #
    #                                               #
    # This config should work on Windows            #
    # or Linux/BSD systems.  Remember on            #
    # Windows to quote pathnames and use            #
    # double backslashes, e.g.:                     #
    # "C:\\Program Files\\OpenVPN\\config\\foo.key" #
    #                                               #
    # Comments are preceded with '#' or ';'         #
    #################################################
    
    # Which local IP address should OpenVPN
    # listen on? (optional)
    ;local a.b.c.d
    
    # Which TCP/UDP port should OpenVPN listen on?
    # If you want to run multiple OpenVPN instances
    # on the same machine, use a different port
    # number for each one.  You will need to
    # open up this port on your firewall.
    port 1194
    
    # SSL/TLS root certificate (ca), certificate
    # (cert), and private key (key).  Each client
    # and the server must have their own cert and
    # key file.  The server and all clients will
    # use the same ca file.
    #
    # See the "easy-rsa" directory for a series
    # of scripts for generating RSA certificates
    # and private keys.  Remember to use
    # a unique Common Name for the server
    # and each of the client certificates.
    #
    # Any X509 key management system can be used.
    # OpenVPN can also use a PKCS #12 formatted key file
    # (see "pkcs12" directive in man page).
    ca ca.crt
    cert server.crt
    key server.key  # This file should be kept secret
    
    # Diffie hellman parameters.
    # Generate your own with:
    #   openssl dhparam -out dh2048.pem 2048
    dh dh2048.pem
    
    dev tun
    
    # supply a VPN subnet
    # for OpenVPN to draw client addresses from.
    # The server will take 10.8.0.1 for itself,
    # the rest will be made available to clients.
    # Each client will be able to reach the server
    # on 10.8.0.1. Comment this line out if you are
    # ethernet bridging. See the man page for more info.
    server 10.8.0.0 255.255.255.0
    
    
    
    # Push routes to the client to allow it
    # to reach other private subnets behind
    # the server.  Remember that these
    # private subnets will also need
    # to know to route the OpenVPN client
    # address pool (10.8.0.0/255.255.255.0)
    # back to the OpenVPN server.
    push "route 192.168.15.0 255.255.255.0"
    
    
    # If enabled, this directive will configure
    # all clients to redirect their default
    # network gateway through the VPN, causing
    # all IP traffic such as web browsing and
    # and DNS lookups to go through the VPN
    # (The OpenVPN server machine may need to NAT
    # or bridge the TUN/TAP interface to the internet
    # in order for this to work properly).
    push "redirect-gateway def1"
    
    # Certain Windows-specific network settings
    # can be pushed to clients, such as DNS
    # or WINS server addresses.  CAVEAT:
    # [http://openvpn.net/faq.html#dhcpcaveats](http://openvpn.net/faq.html#dhcpcaveats)
    # The addresses below refer to the public
    # DNS servers provided by opendns.com.
    push "dhcp-option DNS 192.168.15.102"
    #push "dhcp-option DOMAIN TAGE.local"
    
    keepalive 10 120
    
    
    # Enable compression on the VPN link.
    # If you enable it here, you must also
    # enable it in the client config file.
    comp-lzo
    
    
    # It's a good idea to reduce the OpenVPN
    # daemon's privileges after initialization.
    #
    # You can uncomment this out on
    # non-Windows systems.
    user nobody
    group nogroup
    
    
    # Output a short status file showing
    # current connections, truncated
    # and rewritten every minute.
    status openvpn-status.log
```







[B]
**Client conf file with omitted keys**
[/B]
```

    ##############################################
    # Sample client-side OpenVPN 2.0 config file #
    # for connecting to multi-client server.     #
    #                                            #
    # This configuration can be used by multiple #
    # clients, however each client should have   #
    # its own cert and key files.                #
    #                                            #
    # On Windows, you might want to rename this  #
    # file so it has a .ovpn extension           #
    ##############################################
    
    # Specify that we are a client and that we
    # will be pulling certain config file directives
    # from the server.
    client
    
    # Use the same setting as you are using on
    # the server.
    # On most systems, the VPN will not function
    # unless you partially or fully disable
    # the firewall for the TUN/TAP interface.
    ;dev tap
    dev tun
    
    # Windows needs the TAP-Win32 adapter name
    # from the Network Connections panel
    # if you have more than one.  On XP SP2,
    # you may need to disable the firewall
    # for the TAP adapter.
    #dev-node MyTap
    
    # Are we connecting to a TCP or
    # UDP server?  Use the same setting as
    # on the server.
    ;proto tcp
    proto udp
    
    # The hostname/IP and port of the server.
    # You can have multiple remote entries
    # to load balance between the servers.
    remote 81.146.22.163 1194
    ;remote my-server-2 1194
    
    # Choose a random host from the remote
    # list for load-balancing.  Otherwise
    # try hosts in the order specified.
    ;remote-random
    
    # Keep trying indefinitely to resolve the
    # host name of the OpenVPN server.  Very useful
    # on machines which are not permanently connected
    # to the internet such as laptops.
    resolv-retry infinite
    
    # Most clients don't need to bind to
    # a specific local port number.
    nobind
    
    # Downgrade privileges after initialization (non-Windows only)
    user nobody
    group nogroup
    
    # Try to preserve some state across restarts.
    persist-key
    persist-tun
    
    # If you are connecting through an
    # HTTP proxy to reach the actual OpenVPN
    # server, put the proxy server/IP and
    # port number here.  See the man page
    # if your proxy server requires
    # authentication.
    ;http-proxy-retry # retry on connection failures
    ;http-proxy [proxy server] [proxy port #]
    
    # Wireless networks often produce a lot
    # of duplicate packets.  Set this flag
    # to silence duplicate packet warnings.
    ;mute-replay-warnings
    
    # SSL/TLS parms.
    # See the server config file for more
    # description.  It's best to use
    # a separate .crt/.key file pair
    # for each client.  A single ca
    # file can be used for all clients.
    #ca ca.crt
    #cert client.crt
    #key client.key
    
    # Verify server certificate by checking that the
    # certicate has the correct key usage set.
    # This is an important precaution to protect against
    # a potential attack discussed here:
    #  [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm)
    #
    # To use this feature, you will need to generate
    # your server certificates with the keyUsage set to
    #   digitalSignature, keyEncipherment
    # and the extendedKeyUsage to
    #   serverAuth
    # EasyRSA can do this for you.
    remote-cert-tls server
    
    # If a tls-auth key is used on the server
    # then every client must also have the key.
    ;tls-auth ta.key 1
    
    # Select a cryptographic cipher.
    # If the cipher option is used on the server
    # then you must also specify it here.
    ;cipher x
    
    # Enable compression on the VPN link.
    # Don't enable this unless it is also
    # enabled in the server config file.
    comp-lzo
    
    route add 192.168.0.0 mask 255.255.255.0 gw 192.168.0.1
    
    # Set log file verbosity.
    verb 3
    
    # Silence repeating messages
    ;mute 20
```




I have tried a variety of "fixes" that I have gleamed from the net but not luck, for example from here


[http://ubuntuforums.org/showthread.php?t=1660520](http://ubuntuforums.org/showthread.php?t=1660520)


and


[http://ubuntuforums.org/showthread.php?t=2168279](http://ubuntuforums.org/showthread.php?t=2168279)


as well as various others


Thanks in advance

---

