---
title: "problems in socket programming"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by dwnlds on 2011-01-11
> Hello Hi,
I am new to the socket programming. 
can any one tell me what is is the problem in server.c and client.c program.

Error i am getting is : "Network not reachable" during connect() function in client.c

Both server.c and client.c is shown below
Client.c
```

/*
    Name:    01_client.c
    Description:    Demo for client server communication using sockets
*/
#include<stdio.h>
#include<stdlib.h>
#include<arpa/inet.h>
#include<sys/types.h>
#include<sys/socket.h>


#define SERVER_IPADDR 127.0.0.1
#define PORT_NUMBER 7891

main(int argc,char **argv)
{
    printf("Socket file creation\n");
    int cfd;
    cfd=socket(AF_INET,SOCK_STREAM,0);
    if(cfd==-1)
    {
        perror("creation:");
        exit(1);
    }    
    struct sockaddr_in ser;
    //int l;
    ser.sin_family=AF_INET;
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port= PORT_NUMBER;    //htons(PORT_NUMBER);
    ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");
    //l=sizeof(ser);
    printf("Port Number: %d\n",ser.sin_port);
    int l=sizeof(ser);
    int r=connect(cfd,(struct sockaddr *)&ser,l);        //sizeof(ser));
    if(r==-1)
    {
        perror("Connection:");
        exit(1);
    }
    char buf[]="I am connected to you";
    write(cfd,buf,sizeof(buf));
    r=read(cfd,buf,sizeof(buf));
    write(cfd,buf,r);
    close(cfd);
}
```Server.c
```
/*
    Name:        01_server.c
    Description:    Demo program for server-client communication using socket API.
*/

#include<stdio.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<stdlib.h>
#include<string.h>
#include<arpa/inet.h>
/* Loop Back Addr*/

#define SERVER_IPADDR 127.0.0.1        
#define DEFAULT_PROTOCOL 0
#define PORT_NUMBER 7891

main(int argc,char *argv[])
{
    int sfd;
    printf("Creating Socket file\n");
    sfd=socket(AF_INET,SOCK_STREAM,DEFAULT_PROTOCOL);            /*Step 1 socket file creation.*/
     if(sfd==-1)
    {    perror("Unable to creat server socket file:");
        exit(1);
    }
    printf("Binding the socket file\n");
    struct sockaddr_in ser;                            /*Step 2: Initializing the socket file*/
    ser.sin_family=AF_INET;                            /*      binding the Port number and IP Address of server*/
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port=PORT_NUMBER;    //htons(PORT_NUMBER);
    ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");

    printf("PortNumber: %d\n",ser.sin_port);

    if(bind(sfd,(struct sockaddr *)&ser,sizeof(ser))==-1)
    {    perror("Change port address:");
        exit(2);
    }

    printf("Listen initializing the socket file");
    listen(sfd,10);                                /*Step 4: Listening the Clients */
    int    l,cli_fd;
    struct sockaddr_in cli;
    l=sizeof(cli);
    printf("Accepting the clients");
    cli_fd=accept(sfd,(struct sockaddr *)&cli,&l);                /*Step 5: Accepting the clients*/    
    
    printf("Client IP Addesss: %s\n",inet_ntoa(cli.sin_addr));
    printf("Client Port Number:%d\n",ntohs(cli.sin_port));
    char buf[512];
    strcpy(buf,"Welcome to Server System");
    printf("Send the data client");
    write(cli_fd,buf,sizeof(buf));            /*Step 6: Transmitting Data to client*/
    int r=read(sfd,buf,sizeof(buf));
    write(1,buf,r);
    close(sfd);
    close(cli_fd);
    //return 0;
}


```

---

### Post by HDave on 2011-01-11
These forums are for help with the Ubuntu Linux operating system.  You need to ask this question on a programming forum such as [StackOverflow]("www.stackoverflow.com")

---

### Post by gmargo on 2011-01-11
Duplicate thread.
The good stuff is over at 
[http://ubuntuforums.org/showthread.php?t=1663933](http://ubuntuforums.org/showthread.php?t=1663933)

---

