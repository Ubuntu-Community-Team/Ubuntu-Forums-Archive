---
title: "502 Bad Gateway Nginx  dotnet Core 7"
date: 2023-11-26
forum: Networking &amp; Wireless
---

### Post by tonysar on 2023-11-26
Hello all . 
Running Ubuntu 23 vps . 
I have installed dotnet core 7 + ASP.Net . that are required by nopCommerce . as directed by tutorials , i have setup Nginx as reverse proxy , At this point , everything work well, however, nopcommerce requires application restart when some changes are dose from admin 
this is the time when i get 502 Bad Gateway , error. daemon has been created and restarts the application successfully after 10 second, which allow me to access both front and back end of the site. 
Nginx Error logs shows Connection refused while connecting to upstream client, which i believe is application server ( dotnet ) . 
I have also ran the following command on my server . 

dotnet /var/www/nopcommerce/Nop.Web.dll 
I get following result 

```

Unhandled exception. System.IO.DirectoryNotFoundException: /home/User_name/Themes/
   at Microsoft.Extensions.FileProviders.PhysicalFileProvider..ctor(String root, ExclusionFilters filters)
   at Nop.Web.Framework.Infrastructure.Extensions.ApplicationBuilderExtensions.UseNopWebOptimizer(IApplicationBuilder application)
   at Nop.Web.Framework.Infrastructure.NopStaticFilesStartup.Configure(IApplicationBuilder application)
   at Nop.Core.Infrastructure.NopEngine.ConfigureRequestPipeline(IApplicationBuilder application)
   at Nop.Web.Framework.Infrastructure.Extensions.ApplicationBuilderExtensions.ConfigureRequestPipeline(IApplicationBuilder application)
   at Program.<Main>$(String[] args)
Aborted (core dumped)

```

As you can see in first line of error : system is looking at home directory of user for Themes .. rather then to /var/www/nopcommerce/Themes , any reason for this path? or can this be changed somewhere in ubuntu . ? 

Thanks.

---

