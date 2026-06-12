---
title: "Tor config: do I need polipo AND privoxy along with tor ?"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by Cbhihe on 2014-10-22
Hi, I am reviewing my options to make an educated guess prior to installing [FONT=courier new]tor[/FONT] along with [FONT=courier new]obfsproxy[/FONT] from the Ubuntu Software Center and [FONT=courier new]selektor[/FONT] as GUI from. My query concerns the possible use and added advantages of  [FONT=courier new]polipo [/FONT][COLOR=#ff0000]AND/OR[/COLOR]  [FONT=courier new]privoxy[/FONT]. 
I will be using the lot with a stand-alone [FONT=courier new]Firefox v.33.0 [/FONT]browser. I.e. I don't want the TBB all-in-one tar ball. 

As I understand from a spate of posts all other the net and web pages from a good 6~7 sites, all devoted to either to the question:
 - [FONT=courier new]polipo v.1.0.4.1-6[/FONT] is a web proxy and proxy server that also provides web caching (and ad-zapping)
 - [FONT=courier new]privoxy v.3.0.21-2[/FONT] is a proxy server (and an ad/banner/pop-up blocker and a cookie mgr)

**Q)** Do I really need either of the above, as proxy-server(s), in order to achieve surfing-anonymity ?
[FONT=courier new]Firefox[/FONT] is , not only socks ready (v4 and v5) but also proxy-ready.  
I have an ill-defined hunch (because I don't understand all this thorougly - no doubt)  that if I punch in [FONT=arial narrow]IP 127.0.0.1:9050[/FONT] as manual proxy in [FONT=courier new]Firefox[/FONT], it will actually be able to work fine with [FONT=courier new]tor[/FONT]. This is what *@NobodyNessie* implicitly points out in post #5 of [this thread]("http://ubuntuforums.org/showthread.php?t=2229846&highlight=polipo+privoxy"). Since I have ad/banner and cookie-blocking software ([FONT=courier new]AdBlock plus Popup addon[/FONT], [FONT=courier new]AdBlock Plus[/FONT], [FONT=courier new]BetterPrivacy[/FONT]) as well as [FONT=courier new]NoScript[/FONT] properly configured in my usual instance of [FONT=courier new]Firefox[/FONT], what would either[FONT=courier new]  privoxy[/FONT]  or [FONT=courier new]polipo[/FONT] really bring ?

**Q)** What would be the added value to using either [FONT=courier new]privoxy[/FONT] or [FONT=courier new]polipo[/FONT] *or _both_*  ?
If insalling/configuring privoxy meant getting rid of AdBlock Plus, ABP PopUp Addon and BetterPrivacy, I would not mind although that, strictly speaking, would not constitute added value, just less clutter in my Firefox addons' list.

**Q)** Would using both not be a complete overkill (all at the cost of increased latency of course, but it is not the issue here) ? 
(I am asking this last question, thinking that perhaps one interesting characteristic of polipo ist its (unlimited but "limit-able) cache mgt, but I am not quite sure of even that). 

Can somebody help alleviate my misery by answering ?
-ced

---

### Post by MechaMechanism on 2014-10-23
[FONT=courier new]Polipo[/FONT] is the officially supported software while [FONT=courier new]privoxy [/FONT]is an option.  Go with [FONT=courier new]polipo.  Both are about the same.  However [FONT=courier new]Polipo is simpler to set up.  Also only use one or the other, but not both.[/FONT][/FONT]

---

### Post by Cbhihe on 2014-10-23
@MechaMechanism: Thanks for your imput, but what do you mean by ? > *[FONT=courier new]polipo[/FONT] is the officially supported soft while [FONT=courier new]privoxy[/FONT] is an option.* From the [FONT=courier new]software-center [/FONT], you can read:
> For Polipo:
*Canonical does not provide updates for Lightweight, caching web proxy. Some updates may be provided by the Ubuntu community.*
For Privoxy:
Canonical does not provide updates for Privacy enhancing HTTP Proxy. Some updates may be provided by the Ubuntu community.
Both are provided as options and are placed on the same footing, when installing[FONT=courier new] tor [/FONT]from the [FONT=courier new]software-center[/FONT]. 
I don't dispute that either polipo or privoxy are good.
I am really asking: ***why install one and not the other, or both or none** ?*

---

### Post by Steven_Williams on 2014-10-23
If you are just looking to use Firefox to browse anonymously you could just grab the Tor Browser Bundle and fire that up. Its version of Firefox doesn't support things like flash, but you can after starting it just use your normal Firefox pointed to 127.0.0.1:[3128 if I recall correctly otherwise 9050].

---

### Post by MechaMechanism on 2014-10-23
> **Cbhihe said:**
> @MechaMechanism: Thanks for your imput, but what do you mean by ?  From the [FONT=courier new]software-center [/FONT], you can read:

Both are provided as options and are placed on the same footing, when installing[FONT=courier new] tor [/FONT]from the [FONT=courier new]software-center[/FONT]. 
I don't dispute that either polipo or privoxy are good.
I am really asking: ***why install one and not the other, or both or none** ?*

I just mean the Tor project itself has moved to polipo.  In Ubuntu polipo and privoxy are in universe.  So it's Tor that recommends polipo.  Why, I don't know.

---

### Post by Forbees on 2014-10-23
> **Steven_Williams said:**
> If you are just looking to use Firefox to browse anonymously you could just grab the Tor Browser Bundle and fire that up. Its version of Firefox doesn't support things like flash, but you can after starting it just use your normal Firefox pointed to 127.0.0.1:[3128 if I recall correctly otherwise 9050].

if i remember correctly tor recommends using the browser bundle regardless. unless you plan on using tor not just through a browser, just get the bundle

---

