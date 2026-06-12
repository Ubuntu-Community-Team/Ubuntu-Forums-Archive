---
title: "ulimit for the hungry Beagle"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by knobuddixspexdazpanishinq on 2009-01-12
Hi all,

I want to prevent Beagle [Installed: 0.3.8-1ubuntu2] from utilising 100% of my (tiny) memory and my swap because it prevents me from doing anything else concurrently. 
[Ubuntu 8.10, memory 502.1 MiB, swap is approx 1.5 GB]. 

From researching my problem **ulimit** should provide a solution, but for a baby-stepper like me, man pages are confusing. eg: "*Values are in 1024-byte increments, except for `-t', which is in seconds, `-p', which is in units of 512-byte blocks, and `-n' and `-u', which are unscaled values.*":confused:

My questions are: How can I query what my total virtual memory is with ulimit? or How do I find my total virtual memory in the values that ulimit requires?
and
Can I then stipulate a ceiling of 75% of my memory and 75% of my swap for Beagle to utilise and if so what is the syntax for this recipe?

cheers,
M

---

