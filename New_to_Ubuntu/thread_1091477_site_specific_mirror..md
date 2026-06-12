---
title: "site specific mirror."
date: 2009-03-09
forum: New to Ubuntu
---

### Post by bobdabuilder on 2009-03-09
My very silly project...
have to build an application that caches the results of students from the site [results.vtu.ac.in]("http://www.results.vtu.ac.in") and store it in the college proxy server. which can then be accessed by anyone connected to this network under the proxy server.

+ to get the results we have to enter the USN(university Serial Number)

+ the Results that are supposed to be cached are only the students of the  college(not the entire results VTU(vishvesharia Technological University).
+ These results are then provided to the college students directly from the college server, using a website like interface.
+ Also this will send the results of a student directly to their E-Mail id.

My questions are...
** How will i cache the results of the students?
    (  there is this command called wget that is able to just save pages. Should i just write a shell script that keeps on getting the results for the USN's )... Please suggest how to go about this... or any other methods. ????

** how can i send the results to the E-Mail id of the student.
(planned of using PERL to send.. but still do not know how to)  is there an already written code that handles the mailing.

** what are the other things i have to look into while implementing this ???

Thank you for spending time. 
Any suggestions, clarifications are welcome and i'll be greatful.

---

### Post by stanz on 2009-03-10
sounds like a database with user details would help.
a cron job to mail gathered info--to where ya need it.

i liked working with mysql...

---

