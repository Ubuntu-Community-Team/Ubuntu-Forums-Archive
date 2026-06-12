---
title: "Using nginx as reverse proxy for docker containers"
date: 2019-12-06
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2019-12-06
Hi all!

I am trying to connect a locally installed Nginx service as my reverse proxy for multiple docker containers running their own Tomcat 8.5 images.
I have a local nginx and tomcat 8.5 installation with multiple virtual hosts that works as expected, i can reach all my sites.

I have than stopped the local tomcat service, started docker service and created a container with tomcat:8.5.49-jdk11-openjdk

```
docker run -d -it --entrypoint /bin/bash --name test1 -p 127.0.0.1:8080:8080 tomcat:8.5.49-jdk11-openjdk
```

But nginx gives a HTTP-502 back.


My Nginx configuration is as follows
```

server {
        listen 80;

        server_name test.local;

        location / {
                proxy_pass                 http://127.0.0.1:8080;
                proxy_set_header        Host $http_host;
                proxy_set_header        X-Real-IP $remote_addr;
                proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header        X-Forwarded-Proto $scheme;
        }

        error_page 502 /502.html;
        location = /502.html {
                root /usr/share/nginx/html;
                internal;
        }
}

```

If i stop the container, start my local tomcat server everything works.

What am i missing? :)

Thanks in advance
Best regards!

---

### Post by TheFu on 2019-12-06
I use something like this:
```

upstream alaskaproxy {
        server 172.22.22.4:8181;
}
server {

   access_log  /var/log/nginx/alaska.access.log;
   error_log  /var/log/nginx/alaska.error.log;
   server_tokens off;
   listen   80;
   server_name  ak.example.com;
   add_header X-Frame-Options SAMEORIGIN;
   add_header X-Content-Type-Options nosniff;
   add_header X-XSS-Protection "1; mode=block";
   location / {
      gzip on;
      gzip_static on;
                try_files index.shtml index.html @alaskaproxy ;
    }

        location @alaskaproxy {
                gzip              on;
                gzip_static       on;
                gzip_min_length   1000;
                gzip_vary         on;
                gzip_buffers      16 8k;
                gzip_comp_level   6;
                gzip_http_version 1.0;
                gzip_types        text/plain text/css image/x-icon application/x-perl application/x-httpd-cgi;
                proxy_set_header  X-Real-IP  $remote_addr;
                proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header  Host $http_host;
                proxy_pass    http://alaskaproxy;
        }
}
```
This is converted from HTTPS setup. Don't have any non-HTTPS setups anymore.  I use nginx as the SSL terminator. The back ends are not using HTTPS.

I removed some micro-caching stuff. It requires setup in other files and directories.

The key is the "upstream" part.

---

### Post by Drenriza on 2019-12-06
Hi TheFu thanks for the reply.
It makes sense, but i dont see the difference from my own setup that i would say "Aaaaaa that explains it".
The upstream server resolves to [http://172.22.22.4:8181;](http://172.22.22.4:8181;) as i do in my proxy pass for [http://127.0.0.1:8080;](http://127.0.0.1:8080;)

It works on my local tomcat, but for some reason nginx returns HTTP-502 when used with docker.
Tomcat just contains the ROOT folder where i first deleted the manager project and associated files, and added my ROOT.war file through my Dockerfile


```

FROM tomcat:tomcat-8.5-openjdk-template

MAINTAINER ME "me@me.me"

ADD ROOT /usr/local/tomcat/webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]

```

With a standard entry in /conf/server.xml with an <Alias> that matches my nginx server_name.

Are there some docker network i need to open for on the local machine before it can communicate with Nginx that resides
outside of docker?

The docker container listens for 8080 and my nginx forwards to 127.0.0.1:8080, is there something i need to bridge? Slinging ideas around here.

---

### Post by TheFu on 2019-12-06
Just posted what works here for my 20 webapp servers or so.  Take what works.

If tomcat is already listening on 8080, then that port can't be used for docker.  Why not change the docker port to 8081?
I don't use either tomcat nor docker. Reasons.

---

### Post by Drenriza on 2019-12-09
> Just posted what works here for my 20 webapp servers or so.  Take what works.
Thanks @TheFu

I dont know exactly what went wrong, but after i started using ports in the 5000X range, it started to work.
Also thanks for your Nginx example, i will definitely look at that to upgrade my own setup, real-world examples are always great inspiration.

Curious though, why dont you use Docker or Tomcat?
And what do you use instead?

Thanks for the help and inspiration!
Best regards.

---

### Post by slickymaster on 2019-12-09
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2019-12-09
> **Drenriza said:**
> Thanks @TheFu

I dont know exactly what went wrong, but after i started using ports in the 5000X range, it started to work.
Also thanks for your Nginx example, i will definitely look at that to upgrade my own setup, real-world examples are always great inspiration.

Curious though, why dont you use Docker or Tomcat?
And what do you use instead?

So you retained the same config you already had, but just pointed to different ports?  I have to use the backends because there are usually multiple load balanced servers, not just a simple 1-to-1 proxy.

We avoid using Java, so we don't use Tomcat. First introduced to it in the mid-1990s by SunM.  At the time, they knew it was slow and bloated.  Believed it would mature, become as fast as C++ and almost as good with RAM while being more secure.  That was around 1996.   I'm still waiting.  I did look into Java for about a year, but at the time it wasn't ready, so we dropped Java.  By the time Java was ready for production use (even with all the bloat and slowness), I'd moved on to technical architecture.  The security claims never seemed to happened either.  A number of my coworkers from the mid-1990s became professional Java software developers.  We still argue about how bloated and slow it is.  They all work in largish corporations and work on legacy software.
I work at a small company, part time, after retiring from a technical architect and enterprise architecture job at a Fortune 10 company.  They used lots of java there. Sometimes for desktop applications which were all bloated and slow.  For webapps, Java is my last choice of language. I'd rather see almost any other language used.

Docker is the wordpress of containers.  As the most popular solution, it is also the most attacked.  I've been doing virtualization since the late 1990s.  Small scale and large scale, though not with thousands and thousands of servers.  Docker has always had a number of critical security issues, but has a history of claiming greater security than it truly provides.  Other containers types don't seem to have that same issue. Perhaps docker is attacked more often, like wordpress, so we get to learn about the issues. Or perhaps the other container design and development teams are just better at security?  I don't know which.  Docker certainly has won the marketing part of this event.

On Ubuntu, we can use LXD instead of docker.  It is fast, efficient, and doesn't seem to have the same security issues as docker.  The idea that someone would download an entire docker container created by someone unknown freaks me out.  If you use docker, please, please, build your own containers, so you understand what is inside, the settings, and the dependencies which need to be constantly updated.  Almost all docker deployments that aren't 100% completely replaced every few weeks are out of date, since 1 of the dependencies inside that container will have a patch.  Inside a corporate LAN, monthly or quarterly updates might be sufficient. On the internet, 2 weeks is pushing the delay.  The deployment of containers for internet use needs to be automatic, and start by rebuilding all the dependencies for the container.

If you are interested in best practices for containers and container security, a number of Linux conferences have covered that stuff over the last 5 yrs.  Many of the conferences record sessions and post to youtube.  Look for talks by Joe Brockmeier, Thomas Cameron, Jose Antonio, and  Michael Solberg. I've attended their talks.

---

### Post by Drenriza on 2019-12-10
> **TheFu said:**
> So you retained the same config you already had, but just pointed to different ports?
Yes, i am not really sure why that worked since there were no conflicts before the change either.

Thanks alot for reference to the talks on YouTube @TheFu, that is highly appreciated.
Currently i am looking into container technology with no starting point besides Docker being referenced alot, so that is my first stop and test-base.

I agree when downloading Docker images from person X, caution should always be exercised.
Luckily so far, all the official images for services i use is there.

Currently i have 4 partial days of experience in this area :)

Also thanks for the real-world experience and thoughts on Java!
I have used Java as a Hobby and for learning about the terms of programming, what is OOP, objects, design patterns with more which has been great.
At some point i was casually asked "Hey, can you create X?" and from there things have been slowly developing.

I didn't want to get vendor locked with C# and Mono back in the day was not that great.
PHP was not for me, i would rather sit in a server room all day.

Best regards

---

