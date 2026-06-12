---
title: "What personal information sent to VPN server to initialize an open VPN?"
date: 2024-05-13
forum: Networking &amp; Wireless
---

### Post by usoviet on 2024-05-13
What personal information (like hostname etc) of Ubuntu sends in order to initialization of open VPN (establishing)?

---

### Post by The Cog on 2024-05-13
I imagine that depends entirely on what information the VPN client software chooses to collect and send.The client's real IP address so the VPN server can reply is the only necessity I can think of.

---

### Post by usoviet on 2024-05-13
> **The Cog said:**
> I imagine that depends entirely on what information the VPN client software chooses to collect and send.The client's real IP address so the VPN server can reply is the only necessity I can think of.

An ovpn file is imported by the Ubuntu Setting panel (Control center?), no other client needed.

---

### Post by TheFu on 2024-05-13
ovpn is just text.  Look inside.

However, the VPN provider does have access to all unencrypted traffic going through its pipes and if encrypted traffic is poorly encrypted using out of date ciphers (which are still allowed), then they may have complete access to all the data.  Using a VPN provider you trust really is important.  

I'm so paranoid that I don't trust any of them and choose to rent a VPS and install my own VPN server whenever I need a VPN.  Because I do this often, I have the server setup taking less than 3 minutes from the time I log into the VPS panel and start choosing the VPS machine configuration until I'm connected to the VPN and nearly anonymous.  Of course, if the VPS is required by some govt, they can capture all the transferred data and try to crack the TLS encoded packets from inside the vpn tunnel later, if they like.

Some govts are known to require the VPN keys be provided for all VPNs under their control.  For them, all the data is available.  
Some govts require older versions of TLS (the newer version of SSL) be used which have been cracked, so all that data is available to them as well.  

If you really need the protections of a VPN and live in the places that don't allow privacy to that level, perhaps a different solution than a VPN would be prudent?  TOR would be my first go-to tool, but performance can be bad.

---

### Post by usoviet on 2024-05-15
I suspect that too, so I use the method of VPN on Tor, so my real IP is still hidden to VPN server. I just want to know what the system information can help them identify me are not a different user (eg, computer name) when the tor IP are different.

---

### Post by currentshaft on 2024-05-15
tag

---

### Post by TheFu on 2024-05-15
> **usoviet said:**
> I suspect that too, so I use the method of VPN on Tor, so my real IP is still hidden to VPN server. I just want to know what the system information can help them identify me are not a different user (eg, computer name) when the tor IP are different.

Tor is only for HTTP/HTTPS traffic.  I don't even know if they tunnel DNS.  They definitely do not tunnel all other traffic ... unless there is another Tor setting.

VPNs are for all ports, if correctly configured and you aren't on MS-Windows (which has a DNS attack for all VPNs announced a few weeks ago, that has been in the code over a decade (perhaps 2)).

More isn't always better.  It often provides a false sense of security rather than real security.  Additionally, Tor cannot help if you've every connected to the same websites using the same userid. Or if you post with the same writing style, just writing style can out you, even from different userids and different IPs.

Privacy on the internet is hard.

---

### Post by usoviet on 2024-05-16
I am using Ubuntu + Whonix-gateway, so DNS resolving is not a problem. Because is OpenVPN file is public using, I guess they cannot identify me if no more personal information OpenVPN sending to the VPN service during initializing connection (about 5 seconds).

---

### Post by TheFu on 2024-05-16
> **usoviet said:**
> I am using Ubuntu + Whonix-gateway, so DNS resolving is not a problem. 

That's no guarantee.

> **usoviet said:**
> 
Because is OpenVPN file is public using, I guess they cannot identify me if no more personal information OpenVPN sending to the VPN service during initializing connection (about 5 seconds).

It isn't that easy.  Behavior matters, assuming everything else is done correctly too.  You can be determined just by behavior. Heck, most browsers can be "fingerprinted" to drastically reduce the number of possible people.  I did a fingerprinting exercise and was able to figure out that only 2 people in Australia, outside Sidney, would have the same fingerprint as my browser.  Just two!  That means in about 22 million people (I removed Sidney's population), just 2 browsers are like mine.  2 locations to knock on the door.   Add in behavior and I bet the other guy would be eliminated - so 1 house.

Browsers give away all sorts of things about us, by default, unless we go out of our way to lie or prevent it.  Things like timezones, languages, addons, extensions, if they allow javascript, then your local LAN can be scanned for other devices using javascript.  Now they have MAC addresses not just for the computer, but for any other devices on the LAN.  MAC addresses can be spoofed on computers, if the NIC allows that, but not on TVs and other IoT devices.  

Like I said, privacy is hard.

---

### Post by currentshaft on 2024-05-17
<34

---

### Post by TheFu on 2024-05-17
> **currentshaft said:**
> Tor has no idea what traffic you're sending, whether it's HTTP or HTTPS or something else. It's not "only for" anything - it's a low latency anonymizing network.

And of course Tor handles DNS, if it didn't, it would be a massive privacy hole.

My reading says that traffic outside the Tor Browser needs to be specifically setup to use Tor.  Looks like there is a per-application method to have each use Tor for networking, but it isn't enabled by default.

[https://support.torproject.org/faq/](https://support.torproject.org/faq/)

---

### Post by usoviet on 2024-05-18
Web browser fingerprint is a long story, now I just want to know what happen during initialization of OpenVPN.

---

### Post by TheFu on 2024-05-18
> **usoviet said:**
> Web browser fingerprint is a long story, now I just want to know what happen during initialization of OpenVPN.

The only way to know for certain is to read the code.  you can try using wireshark, but in theory, no traffic would be sent after the initial challenge setup packets. From that point on, everything should be encrypted, not viewable by us.  "Use the source, Luke."

---

### Post by usoviet on 2024-05-19
I think it is known by some VPN runners. It doesn't need to read the code, but the log.

---

### Post by TheFu on 2024-05-19
> **usoviet said:**
> I think it is known by some VPN runners. It doesn't need to read the code, but the log.

Logs only contain what the programmer chooses.  Usually logs are there to help fine issues, not provide all possible information sent.  What gets logged is only what the programmer coded.

>  The researchers believe it affects all VPN applications when they&#8217;re connected to a hostile network and that there are no ways to prevent such attacks except when the user's VPN runs on Linux or Android. They also said their attack technique _may have been possible since 2002_ and may already have been discovered and used in the wild since then.
Ref: [https://arstechnica.com/security/2024/05/novel-attack-against-virtually-all-vpn-apps-neuters-their-entire-purpose/](https://arstechnica.com/security/2024/05/novel-attack-against-virtually-all-vpn-apps-neuters-their-entire-purpose/)

How much should you trust any VPN?

---

### Post by TheFu on 2024-05-29
US sanctions operators of &#8220;free VPN&#8221; that routed crime traffic through user PCs
Ref: [https://arstechnica.com/security/2024/05/us-sanctions-operators-of-free-vpn-that-routed-crime-traffic-through-user-pcs/](https://arstechnica.com/security/2024/05/us-sanctions-operators-of-free-vpn-that-routed-crime-traffic-through-user-pcs/) 

Be careful which VPN service you choose.

---

### Post by usoviet on 2024-05-29
> **TheFu said:**
> US sanctions operators of “free VPN” that routed crime traffic through user PCs
Ref: [https://arstechnica.com/security/2024/05/us-sanctions-operators-of-free-vpn-that-routed-crime-traffic-through-user-pcs/](https://arstechnica.com/security/2024/05/us-sanctions-operators-of-free-vpn-that-routed-crime-traffic-through-user-pcs/) 

Be careful which VPN service you choose.

That's why I ask.

---

### Post by TheFu on 2024-05-29
> **usoviet said:**
> That's why I ask.

A VPN server has complete access to all packets sent through the tunnel, if they aren't sufficiently encrypted or the encryption keys have been leaked.  Today, we know that all versions of SSL and TLS v1.2 and earlier aren't secure.  

TLS v1.3 has been around a long time.  While I haven't seen any reported cracks for it, at this point, if you really are worried, then I'd assume it has been cracked as well.  You can force your clients to only work with TLS v1.3, but I think clients are setup by default with automatic negotiation for what the server provides, which could easily be lesser versions or completely cracked ciphers from 10+ yrs ago.  

This isn't just about the VPN encryption. It is about the traffic being tunneled too.  Modern browsers allow the user to limit which types of connections they will allow, so there is some control.  You can look up what they allow.

The same problem with VPN servers applies to TOR exit nodes.  Many TOR exit nodes are run by different security services for countries - both as a service AND in the hope they might catch some important data.  Some are known to capture all the data, even if they cannot decrypt it today.  They are storing it for later analysis.   No way do I want my mother's recipes being leaked!   Corporations have a different stance, usually.  They know they can't prevent countries from having access to the encrypted data.  Most countries do not pass on corporate secrets to companies inside their own borders, but a few times, high profile hand-offs have definitely happened.  For most countries, getting access to VPN data is like peaking through a high fence - you can see a bit, but not everything.  In corporate espionage, complete data is stolen and handed over.  I can think of 4 well-known countries that have been caught multiple times doing corporate espionage.  Most, but not all, countries doing it were authoritarian.

Protect your recipes!

---

### Post by Skaperen on 2024-05-29
don't neglect to protect your GRANDmothers' recipes, too.  both of them.  i even have recipes from one of my great grandmothers so i have even more to protect.

---

