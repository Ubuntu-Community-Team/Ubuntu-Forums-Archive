---
title: "I want to save the login info for fvrl.bc.ca, but no browser or extension works"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by bananaboatcoat on 2011-03-02
Hello,


A library site, [https://fvrlhp.fvrl.bc.ca/patroninfo~S0](https://fvrlhp.fvrl.bc.ca/patroninfo~S0), asks for my library card number and PIN. After some time of inactivity, anyone logged on gets automatically logged off.

The website doesn't have an option to "Remember my login". And Firefox, Internet Explorer and Chrome don't offer to save the log-in credentials.

On Chrome, I've tried the ["Autocomplete=on" extension]("https://chrome.google.com/extensions/detail/ecpgkdflcnofdbbkiggklcfmgbnbabhh") for Chrome, but that doesn't work. 


Can somebody please help? We use the [FVRL website]("https://fvrlhp.fvrl.bc.ca/patroninfo~S0") regularly and having to manually type in the very long string of digits that make up the library card is so time-consuming.


What can we do to either force the website to not automatically logout OR have the browser save the library card number and PIN?

Thanks.

---

### Post by coolbrook on 2011-03-02
BBC,

I use Opera for 3 library systems in the GTA.  It works like a charm.

---

### Post by dionysius on 2011-03-03
Same here - if FF, IE and Chrome won't do it get yourself the shiniest version of [Opera]("http://opera.com") and use the built-in password manager. 

Opera is available for Win and Lin; if you're on Ubuntu you could add the [Opera Repository]("http://deb.opera.com/") and you'll automatically get your updates too. 




[SIZE="1"][COLOR="Gray"]Fat cheque from Opera SA still waiting to be cashed[/COLOR][/SIZE]

---

### Post by bananaboatcoat on 2011-03-03
I have just downloaded Opera 11.01 for WinXP. Just like the other browsers, Opera doesn't offer to save the login info.


Can anyone please help?  :(:(:(

I think the FVRL webmasters have done something to the HTML code to make it very very hard to have a browser (any browser) remember (or offer to save) the log-in credentials.

---

### Post by coolbrook on 2011-03-03
I tried logging in and I see that yours is slightly different.  I don't have a valid card number with your system, so I'm not sure if that mattered for me, but I know other systems will allow you to save the card number and PIN whether they're right or not.

Consider contacting the admin and letting them know that you'd like it as an option.  I have the VPL, TPL, Mississauga and Brampton logins and Opera will handle them all.

[https://vpl.bibliocommons.com/user/login](https://vpl.bibliocommons.com/user/login)
[https://www.torontopubliclibrary.ca/signin.jsp](https://www.torontopubliclibrary.ca/signin.jsp)

are examples. FWIW, the library systems here also use the 14-digit card that starts with 2.

---

### Post by JKyleOKC on 2011-03-03
> **bananaboatcoat said:**
> I think the FVRL webmasters have done something to the HTML code to make it very very hard to have a browser (any browser) remember (or offer to save) the log-in credentials.I think you're probably right. I use Firefox myself and have found that different sites behave very differently for its "automatic" login feature, and at least one of my bill-paying sites won't use the saved data at all.

You can probably simplify the problem somewhat by installing a password manager program on your machine, and using it. When I was using Windows for my financial stuff, I used "pwsafe" which keeps a list of my user IDs and passwords for each site (manually entered by me, not automatic), and then launched it in the background when needed. When asked for login data by a site, I could switch to the pwsafe window, copy the user ID to the clipboard, switch back to the browser, paste it in, and then repeat for the password. The pwsafe program automatically cleared the clipboard when shut down, and kept all its data securely encrypted. However using such a tool does pose some security risk, although it tends to be pretty slight for a good tool. You can search Synaptic for "password manager" to see what's available in the repositories...

---

### Post by bananaboatcoat on 2011-03-03
Coolbrook,

FVRL seems to have different HTML code than other library sites. I think looking at other libary sites and saying that they work doesn't help the issue.

---

### Post by bananaboatcoat on 2011-03-03
JKyle,

using the suggested program is no better than having the library card number in a simple notepad application. But I would rather not have to copy and paste every time. It's cumbersome.


I believe that a logged-in websurfer gets automatically logged out from FVRL after X number of minutes on FVRL. Is there a way to make FVRL think that you, the websurfer, are not inactive? For instance, would automatically refreshing a page or automatically (somehow) clicking a link on the page make FVRL think that you are "active" and thus prevent the automatic log-out?

---

### Post by bananaboatcoat on 2011-03-03
> **coolbrook said:**
>  Consider contacting the admin and letting them know that you'd like it as an option. 


I have. And they've explained why they maintain the incovenience:
> 
First, as you know, FVRL offers public Internet access through computers in all of our locations.  If one of our customers were to save their library card number and PIN on one of the public computers, future users would be able to access their account when using the same computer.  We face this problem regularly with web-based e-mail and other account-based web services.
 
Second, most browsers treat the barcode field as a password, rather than a username, making it unreliable in the storage of this information for future use.  More often than not, it results in a “no username” error when the customer tries to log-in a second time using the stored authentication data.  This is beyond our control, as the authentication software is a component of our Integrated Library System, a large, enterprise-level computing solution purchased from a third-party vendor.


---

### Post by JKyleOKC on 2011-03-03
I've seen a little gadget advertised that is supposed to eliminate timing out; it's a dongle that plugs into a USB port, and sends a single-pixel mouse movement once every 20 seconds. That may, or may not, work with your problem. 

You can find out more about it at [http://www.cyberguys.com/product-search/?keyword=jiggler](http://www.cyberguys.com/product-search/?keyword=jiggler) 

I've bought many small items from cyberguys over the past few years and always found them reliable to deal with. Otherwise I have no connection with them.

---

### Post by bananaboatcoat on 2011-03-03
Hmmm, JKyle,

I disbelieve that moving the mouse will be seen by the website. A regular website can't sense mouse movement. It can sense "movement" when something is clicked or when a page is refreshed.

---

### Post by dionysius on 2011-03-03
I've had a look at the source and they've got a time out feature (javascript) but that shouldn't interfere with a browser's password manager. The rest of the source looks normal, there's nothing to indicate why this website won't allow your browser to save your credentials. 

And you're right about websites not sensing movement - websites time out because of inactivity on the server. A few websites that automatically log you out after being 'idle' for a while I usually trick into believing I'm still there by using the 'automatically reload every ... ' function in Opera.

Sorry I can't be of any help :(

---

### Post by bananaboatcoat on 2011-03-03
> **dionysius said:**
> I've had a look at the source and they've got a time out feature (javascript) but that shouldn't interfere with a browser's password manager. The rest of the source looks normal, there's nothing to indicate why this website won't allow your browser to save your credentials. (



1. Whatever is in the html, it _does_ interfere with any browser's ability to save the password/PIN
2. Is there a way to block the javascript that automatically times out?
3. When you looked into the source, did you find out how many minutes it has before it boots a user out?

---

### Post by dionysius on 2011-03-03
> **bananaboatcoat said:**
> 1. Whatever is in the html, it _does_ interfere with any browser's ability to save the password/PIN
2. Is there a way to block the javascript that automatically times out?
3. When you looked into the source, did you find out how many minutes it has before it boots a user out?

1. Maybe someone else could have a look at it as well, I can't find anything.
2. In Opera, right click anywhere on the page, select Edit Site Preferences, Scripting tab, untick Enable JavaScript. Note: disables javascript on the whole site. 
3. 60 minutes.

---

### Post by coolbrook on 2011-03-03
> **bananaboatcoat said:**
> I have. And they've explained why they maintain the incovenience:


Fair enough, but they should have the facility to allow you to save login data on a computer (IP) that isn't within their network.  I have my info saved on my desktop at home and on my notebook which I wirelessly connect to the library while I'm at their location. Neither are public computers per se.  All they need to do is capture the public computers IP address and set up a separate page for those connecting from foreign IPs or the wireless connection.

---

### Post by bananaboatcoat on 2011-03-08
So if the website won't accomodate my request, I have to find some other way. Thus, I ask again: What can I do to both of the following:

1) Have a browser that saves the Library Card Number and the PIN
2) Keep the website from automatically logging me out?

---

