---
title: "Remote Login with XDMCP is not &quot;user-friendly&quot;, we need suggestions..."
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Macchi on 2006-10-13
Dear Ubuntu Fellows!

Remote logins through XDMCP are really great, but the present procedure is neither "user-friendly" nor intuitive for less experienced human users. 

Here is a concrete example:

1) My wife starts the very quiet desktop computer (that is old and slow, the computer, not the wife!). After normal booting a local Ubuntu login screen is presented.

2) At the login screen she has to choose "Options-> Remote Login via X#$*!!" (remember that XDMCP cannot be pronounced by uninitiated users) 

3) She has to wait for approx 4 seconds on a completely blank screen.

4) She gets a window with no explanations for choosing a remote host. The buttons and text are meaningful for a geek but provide few practical clues for a less experienced user.

5) She has to double click on the remote machine, to connect to a faster but noisy application server that is hidden further away in our apartment.

6) Yet another blank screen for 4 seconds.

7) Then she gets a new identical login screen for the server, of course with a different hostname, but this is not so clear for a beginner.

8) Finally my wife can login with username and password.

I would like to be able to choose a remote login directly from the first login screen. The procedure to find remote XDMCP logins could be hidden the user if activated on the client. Then the user only would have to choose a host from a list for local or remote logins.  



ANY SUGGESTIONS ON HOW TO IMPROVE THIS?



That would be solution A.
B) An alternative solution is to provide an extra account for every user, called user2 that upon local login simply starts a fullscreen FreeNX client connetion to the user on the application server. 
C) The other solution would be a complete thin-client solution, 
but I still prefer having a thin+fat client with contents synchronized to the server as a fall back. It allows local login in case the single server stops working. 
D)Finally I could also throw away my 7 computers and buy a fast and quiet Mac, but this is not a question for this forum...

---

### Post by jd65pl on 2006-10-13
I found [this]("https://help.ubuntu.com/community/ThinClientHowto") on how to set-up thisa thin client, it may be of some use.

---

### Post by Macchi on 2006-10-16
Thanks anyway jd65pl for your suggestion on thin clients. I have already seen that before but actually was hoping to get a solution for remote login that is better integrated with the Ubuntu desktop. 

My goal is to get the best of both worlds with a thin-fat client. Then I can normally run the desktop on the server but would also be able to run locally as a fallback solution.

---

