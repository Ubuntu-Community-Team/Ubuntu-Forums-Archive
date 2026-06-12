---
title: "can links in Sylpheed mail be opened with Chrome?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-09
I'm using Sylpheed and I quite like it. The only thing that I can't get is how to - when I click on an web address link in an email - open a link with Chrome. 

In Sylpheed>Configuration>Common Preferences>Details>External Commands I find *sensible-browser '%s'*. If I leave it that way, links are eventually opened with Firefox (although I get an error message first, for some reason). I tried to turn it into *google-chrome '%s'* but it didn't work, ie, nothing happens if I click on the link...

Notice that in System>Preferences>Preferred Applications, the browser is set to Google Chrome and the mail client to Sylpheed. 

Any idea?

---

### Post by al.adab on 2009-12-10
well...

a solution is to replace it with claws-mail 3.6.1 (also for other reasons, mainly because it appears less "buggy)

plus go to 

configuration>preferences>external programs

and replace the mozilla file name with google chrome's: 

*/opt/google/chrome/google-chrome %U*

as well as tick off "use system default when possible".

---

