---
title: "how to configure squid to use ssh tunnel for external sites?"
date: 2018-11-10
forum: Networking &amp; Wireless
---

### Post by kunalv-shah on 2018-11-10
I have a setup where I have ubuntu as squid proxy server at my home. All computers and ipad at my home use that ubuntu as proxy server. Now I want squid to redirect all request to ec2 instance for browsing. For example if I am browsing site [www.example.com](www.example.com) from my home computer, it goes to squid proxy on the same network, now instead of directly serving pages from internet, I want squid proxy to make ssh tunnel to ec2 instance and get pages from [www.example.com](www.example.com) through ec2 instance. EC2 instance is ubuntu again.
I figured out how to configure suqid to cater to my home computers but not sure how should I setup squid to tunnel to ec2 to cater to internet rather than directly going internet. Any pointers here will be helpful.
Attached is the image of my home setup.

[ATTACH=CONFIG]281603[/ATTACH]

---

### Post by slickymaster on 2018-11-10
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by kunalv-shah on 2018-11-10
duly noted.

---

### Post by SeijiSensei on 2018-11-10
Run squid on the remote box and point your browser to it instead.

---

### Post by kunalv-shah on 2018-11-10
That is not possible. Browser on my laptop does not have direct access to remote box.

---

### Post by SeijiSensei on 2018-11-11
Is that by design or just a routing problem?

You can configure a local Squid proxy to forward requests to another proxy upstream.

[https://www.google.com/search?q=squid+forward+to+upstream+proxy](https://www.google.com/search?q=squid+forward+to+upstream+proxy)

---

### Post by kunalv-shah on 2018-11-13
Hi, thanks for the pointer. 
to answer your first question, it is by design. I want to make sure that I use secure connection up till proxy. 

about your pointer to local proxy to upstream proxy. I did take a look at it as a possibility. Just one question on that, is the communication between local proxy and upstream proxy secure? is it possible that someone can do 
"man in the middle" sneaking between two proxies? that was the reason why I wanted to have proxy to ssh tunnel. If local proxy to upstream proxy is as secure as ssh tunnel then this is the perfect solution I am looking for.

---

### Post by SeijiSensei on 2018-11-13
Well, my preference is always to use OpenVPN to create [static tunnels](https://openvpn.net/community-resources/static-key-mini-howto/).  All traffic between the local and remote machines is encrypted.  I assume that would be true for SSH tunnels, but I never use them.

---

### Post by mitesh.agrwl on 2018-11-13
Hi,

> All traffic between the local and remote machines is encrypted. I assume that would be true for SSH tunnels, but I never use them.

The traffic is encrypted in SSH tunnels also. The difference is, OpenVPN uses encryption at layer 3 while SSH uses encryption at Layer 4. Both type of encryption has its own advantages and disadvantages.

---

### Post by kunalv-shah on 2018-11-13
Actually my question was if I have a local proxy which forwards requests to upstream proxy, will the traffic between local proxy and upstream proxy encrypted? If not, I would like some way to secure the communications between local proxy and upstream proxy.

---

### Post by mitesh.agrwl on 2018-11-14
To check that the traffic between local proxy and upstream proxy is encrypted or not, capture the packets on local squid server using [wireshark]("https://www.wireshark.org/") or [tcpdump]("http://www.tcpdump.org/") and analyze them.

---

### Post by SeijiSensei on 2018-11-14
If the traffic between the local and remote proxies is sent through an SSH or Open VPN  tunnel, then it will be encrypted as a matter of course.

---

### Post by TheFu on 2018-11-14
If you want TOR, why not just use TOR?  That's a proxy to a proxy, just controlling the specific exit node.

ssh leaks DNS queries.  I use a ssh-based SOCKS proxy when I'm away from home and don't want to deal with openvpn.  I've posted my ssh-socks-proxy script somewhere here at least once.  It uses port 64000.

OpenVPN is what I use, but there are newer, easier to configure, VPN solutions. They don't have the same time-in-wild proof of security, but at least 1 is being added to the Linux kernel.

I've never tried to have 2 proxies in series.  I'd use a VPN to get to a proxy, if that was even needed 
OR
I'd use TOR.

---

### Post by SeijiSensei on 2018-11-14
> **TheFu said:**
> ssh leaks DNS queries.
I don't care about things like that myself, but wouldn't one solution be to run BIND on the remote and have the clients use that as their default DNS server over the tunnel?

---

### Post by TheFu on 2018-11-14
Default DNS is UDP.  ssh only handles TCP, so if trying to hide DNS (and you probably should), then either use a real VPN that handles **all** traffic or only access sites that in your /etc/hosts or a LAN-based DNS that doesn't leak externally.

Just like GPS data, DNS data provides a huge level of "metadata" for anyone who gains access to that data.  People aren't paranoid enough about metadata.

Of course, everyone has a different level of "security" needs.  My needs probably don't match those for others.  My target security stance is like for a mid-CAP company, not doing any DoD business.  Not quite Fortune 500 and definitely not secure enough to stop state attackers.

IMHO.

---

### Post by kunalv-shah on 2018-11-15
> **SeijiSensei said:**
> If the traffic between the local and remote proxies is sent through an SSH or Open VPN  tunnel, then it will be encrypted as a matter of course.

Exactly, so that is my question. How to configure two proxies so that traffic between local and remote proxy is sent through SSH. Are there any documentation I can refer to ?

Thanks
Kunal

---

### Post by mitesh.agrwl on 2018-11-15
> Exactly, so that is my question. How to configure two proxies so that  traffic between local and remote proxy is sent through SSH. Are there  any documentation I can refer to ?

The OpenVPN or layer three tunnel can be formed between two parties only when both agree to do so. The VPN solution providers set the servers for the client to connect securely. The proxies only forward the request(s) made my the host/local user, hence if the connection is initiated as SSL (read HTTPS connection) then it must forward the same to obtain the reply. As most of the websites support HTTPS only over HTTP, hence, the data is already encrypted. Even still if you want to ensure that the connection is secured by SSL or not, please use the solution provided earlier - wireshark or tcpdump. The best way to understand the network better!

If the Squid server is not used as cache server but only for security purpose, IMO it is better to use a hardware/software [firewall]("https://geekflare.com/best-open-source-firewall/"). They will provide more control over the network, better than proxy server. To manage SSL on squid check the command list in the text file attached.

---

### Post by SeijiSensei on 2018-11-15
> **TheFu said:**
> Default DNS is UDP.  ssh only handles TCP, so if trying to hide DNS (and you probably should), then either use a real VPN that handles **all** traffic or only access sites that in your /etc/hosts or a LAN-based DNS that doesn't leak externally.
I only use OpenVPN tunnels so the UDP/TCP issue doesn't arise.

> **kunalv-shah said:**
> Exactly, so that is my question. How to configure two proxies so that traffic between local and remote proxy is sent through SSH. Are there any documentation I can refer to ?

If you set up an OpenVPN tunnel, each end will have a unique tunnel IP address in addition to its external address.  For instance, on my local machine I have this configuration for OpenVPN:

```

dev tun
remote xxx.xxx.xxx.xxx
ifconfig 10.1.1.30 10.1.1.1
port 43435
secret /etc/openvpn/keys/my.key
[other stuff]

```

That designates the local end of the tunnel as 10.1.1.30 and the remote 10.1.1.1. On the remote the values would be reversed.  I could then configure the local squid to forward requests to the remote squid's 10.1.1.1 address.  Then all the transactions are encrypted by default.

The "port" directive allows you to set a custom port.  Usually I use the same value at both ends.  The value should be >1023 because the connection does not run as the root user.

Again, read this for details: [https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

One more thing.  If you set up such an OpenVPN tunnel, you don't really need two squid caches.  You could simply run squid on the remote machine and point the clients on the local network to its tunnel IP.  You would need to set up a static route on your network so that requests for, say, the 10.1.1.0/24 network would be forwarded to the remote over the tunnel.  On my network, the local OpenVPN machine is just another workstation.  Thus I have added a static route to my router that directs traffic for the 10.1.1.0/24 network to that workstation so it can be forwarded on to the remote.

---

### Post by TheFu on 2018-11-15
I would use a VPN to get to any remote Squid proxy too
or
I'd use TOR.

---

### Post by kunalv-shah on 2018-11-17
so finally between openvpn and ssh I chose openvpn-as. sure it is heavier then SSH but I am sure I am going to use more functionalities of open-vpn as I learn about it. Good thing is that it has module in dd-wrt so in a way my entire home network can be vpn'ed to openvpn-as server I host on google cloud platform. 

Thanks SeijiSensei for the pointers.

---

### Post by TheFu on 2018-11-17
I'd recommend caution in using openvpn on any router.  May want to read up about the pros/cons in doing that first.

I'm confused about going to all these lengths for privacy, but hosting anything on google-cloud.  Very counter intuitive.

---

### Post by kunalv-shah on 2018-11-17
> **TheFu said:**
> I'd recommend caution in using openvpn on any router.  May want to read up about the pros/cons in doing that first. 

Not doing it right now. As I said I may use more features of OpenVPN as I understand the product better.

> **TheFu said:**
>  I'm confused about going to all these lengths for privacy, but hosting anything on google-cloud.  Very counter intuitive.

Had no choice. Due to the configuration of the network my township has, access to my home network is not straightforward. I need to cross three firewalls before I can access my server at home which is not allowed. 

My main requirement was to have a VPN while on travel because I travel and a lot and use hotspots. OpenVPN privatetunnel does not offer servers in India hence connection is very slow if I go to hongkong or EU servers. US servers are out of question. 

I don't see any security risk hosting it on Google. I block all the ports. VPN port is open only for a specific IP. so every time I want to use it, I find public ip and open VPN port only for that IP.

Do you see any risk on that?  What other privacy considerations I should take if I want to host this on Google Cloud ?

---

### Post by mitesh.agrwl on 2018-11-18
> **kunalv-shah said:**
> Not doing it right now. As I said I may use more features of OpenVPN as I understand the product better.



Had no choice. Due to the configuration of the network my township has, access to my home network is not straightforward. I need to cross three firewalls before I can access my server at home which is not allowed. 

My main requirement was to have a VPN while on travel because I travel and a lot and use hotspots. OpenVPN privatetunnel does not offer servers in India hence connection is very slow if I go to hongkong or EU servers. US servers are out of question. 

I don't see any security risk hosting it on Google. I block all the ports. VPN port is open only for a specific IP. so every time I want to use it, I find public ip and open VPN port only for that IP.

Do you see any risk on that?  What other privacy considerations I should take if I want to host this on Google Cloud ?

Please explain your requirements with a diagram? Will be able to provide better solutions when the requirements are clear.

---

### Post by TheFu on 2018-11-18
> **kunalv-shah said:**
> Not doing it right now. As I said I may use more features of OpenVPN as I understand the product better.



Had no choice. Due to the configuration of the network my township has, access to my home network is not straightforward. I need to cross three firewalls before I can access my server at home which is not allowed. 

My main requirement was to have a VPN while on travel because I travel and a lot and use hotspots. OpenVPN privatetunnel does not offer servers in India hence connection is very slow if I go to hongkong or EU servers. US servers are out of question. 

I don't see any security risk hosting it on Google. I block all the ports. VPN port is open only for a specific IP. so every time I want to use it, I find public ip and open VPN port only for that IP.

Do you see any risk on that?  What other privacy considerations I should take if I want to host this on Google Cloud ?

I understand needing to host it externally, but google?  Do you really trust google?   Perhaps I'm spoiled. We have 100 different VPS providers here with 20+ for $5/month or less.   Google makes their money by gathering our data and selling access to it. You are forcing all that data to use their infrastructure as a gateway.  I couldn't get passed that little detail with google as the gatekeeper.
Google knows security, but I just don't trust them on the privacy aspect.  The metadata they capture is scary enough to me. I couldn't imagine providing them with direct access to the data too.
 
But everyone has different comfort levels.

---

### Post by kunalv-shah on 2018-11-19
> **TheFu said:**
> I understand needing to host it externally, but google?  Do you really trust google?   Perhaps I'm spoiled. We have 100 different VPS providers here with 20+ for $5/month or less.   Google makes their money by gathering our data and selling access to it. You are forcing all that data to use their infrastructure as a gateway.  I couldn't get passed that little detail with google as the gatekeeper.
Google knows security, but I just don't trust them on the privacy aspect.  The metadata they capture is scary enough to me. I couldn't imagine providing them with direct access to the data too.
 
But everyone has different comfort levels.

You are right. well actually in India we have only two cloud providers, google and aws. and I have 200$ credit from google so I am trying stuff there and getting taste of things. Once finalised, I may move to other cloud service providers like AWS.

Regarding VPS, I checked with the most and they don't have servers in India and going to Hongkong or EU servers is too much latency.

---

### Post by TheFu on 2018-11-19
[https://www.hostgator.in/vps-hosting](https://www.hostgator.in/vps-hosting)
[https://www.hostinger.in/vps-hosting](https://www.hostinger.in/vps-hosting)
[https://www.fastwebhost.in/vps-hosting.html](https://www.fastwebhost.in/vps-hosting.html)  Rs.175/mo 

Are a few cheap ones. I bet there are hundreds.

---

### Post by mitesh.agrwl on 2018-11-19
> **kunalv-shah said:**
> You are right. well actually in India we have only two cloud providers, google and aws. and I have 200$ credit from google so I am trying stuff there and getting taste of things. Once finalised, I may move to other cloud service providers like AWS.

Regarding VPS, I checked with the most and they don't have servers in India and going to Hongkong or EU servers is too much latency.

If you have data that needs privacy and need to access it from Internet, you can setup your own vpn server on the same machine or on a low price machine (if you are scared to use same for both!). But will cost you a little more with network setup (isp backup). The basic of security is CIA (confidentiality, integrity and accessibility), how much you want to trade one for another!

---

