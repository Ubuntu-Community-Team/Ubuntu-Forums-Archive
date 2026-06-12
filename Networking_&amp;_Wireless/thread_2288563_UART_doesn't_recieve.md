---
title: "UART doesn't recieve"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by mazab.mzb on 2015-07-28
Hi there! I have a little problem with my UART. I'm ussing 2 UART (3 pins) with cross connecting TX-RX and GND. 
The test file *file.txt* has 776 bytes. I can send it in one direction TX-UART0->RX-UART1 perfectly. In reverse (TX-UART1->RX-UART0) I recieve an empty file. 
In debugging time with Hyperterminal I just can read garbage in UART1 TX pin.
I don't understand what I'm doing wrong. Please, help me. 

This is the C code:

```
#include <errno.h>      // Error number definitions#include <stdint.h>     // C99 fixed data types
#include <stdio.h>      // Standard input/output definitions
#include <stdlib.h>     // C standard library
#include <string.h>     // String function definitions
#include <unistd.h>     // UNIX standard function definitions
#include <fcntl.h>      // File control definitions
#include <termios.h>    // POSIX terminal control definitions
#include <sys/types.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <netinet/in.h>
#include <sys/stat.h>
#include <sys/time.h>




#define TAM_MAX 800


// Msg struct
typedef struct{
    int Id;
    int Tam;
    struct timeval tiempo;
    char *Mensaje;
    double checksum;
}Mensaje;

// Answer struct
typedef struct{
    int Id;
    char c;
}Respuesta;


// Open usb-serial port for reading & writing
int open_port(const char *direccion){


    int fd;    // File descriptor for the port
    // configuration options
         // O_RDWR - we need read
         //     and write access
         // O_CTTY - prevent other
         //     input (like keyboard)      
         //     from affecting what we read
         // O_NDELAY - We don't care if     
         //     the other side is           
         //     connected (some devices
         //     don't explicitly connect) 
    fd = open(direccion, O_RDWR | O_NOCTTY | O_NONBLOCK);


    if (fd == -1){
        fprintf(stderr, "Open_port: Unable to open %s %s\n",direccion, strerror(errno));
    }
    return fd;
}


int main(int argc, char **argv){


    int             pd0=0, pd1=0, fd0=0, fd1=0;     // File descriptor
    struct termios  options;    // Terminal options
    int             rc1, rc0;         // Return value
    int             j,leido,c,d;
    int             wordsRead,wordsWritten;
    double             cksum;
    char             buffer0[TAM_MAX], buffer1[TAM_MAX], prebuffer[255];
    char             *p;
    struct timeval     t_ant, t_act;
    
    Mensaje men0, men1;
    men0.Id=1;
    Respuesta res0, res1;
    
    t_ant.tv_sec=0;
    t_ant.tv_usec=0;
    
    pd0 = open_port("/dev/ttyS0");
    pd1 = open_port("/dev/ttyS1");


    // Get the current options for the ports
    if((rc0 = tcgetattr(pd0, &options)) < 0){
        fprintf(stderr, "Failed to get attr: %d, %s\n", pd0, strerror(errno));
        exit(EXIT_FAILURE);
    }


    // Set the baud rates
    cfsetispeed(&options, B115200);


    // Set the baud rates
    cfsetospeed(&options, B115200);


    cfmakeraw(&options);
    // CLOCAL means don't allow
    // control of the port to be changed
    // CREAD says to enable the receiver
    options.c_cflag |= (CLOCAL | CREAD);       // Enable the receiver and set local mode
    options.c_cflag &= ~PARENB;                // Bit de paridad deshabilitado
    options.c_cflag &= ~CSTOPB;                // 1 stop bit (habilitado son 2 bits)
    options.c_cflag &= ~CRTSCTS;               // Disable hardware flow control
    options.c_cflag |= CS8;                    // Palabras de 8 bits
    
    options.c_cc[VMIN]  = 1;
    options.c_cc[VTIME] = 2;


    // Set the new attributes
    if((rc0 = tcsetattr(pd0, TCSANOW, &options)) < 0){
        fprintf(stderr, "failed to set attr: %d, %s\n", pd0, strerror(errno));
        exit(EXIT_FAILURE);
    }


    // Set the new attributes
    if((rc1 = tcsetattr(pd1, TCSANOW, &options)) < 0){
        fprintf(stderr, "failed to set attr: %d, %s\n", pd1, strerror(errno));
        exit(EXIT_FAILURE);
    }
    
    ////////////////////////////////
    // Simple Read/Write Code Here//
    ////////////////////////////////
    
    while(men0.Id<11){    


        gettimeofday(&men0.tiempo, NULL);
        
        
        // STRUCT TO SEND
        p = buffer0;
        memcpy(p, &men0.Id, 4);
        p += 4;
        men0.Tam=776;
        memcpy(p, &men0.Tam, 4);
        p += 4;
        memcpy(p, &men0.tiempo, 8);
        p += 8;
        fd0 = open("file.txt", O_RDONLY);
        leido = read(fd0, men0.Mensaje, men0.Tam);
        close(fd0);
        memcpy(p, &men0.Mensaje, men0.Tam);
        p += men0.Tam;
        men0.checksum=0;
        for(j=0; j<(TAM_MAX-8); j++){
            men0.checksum += (unsigned int)buffer0[j];
        }
        memcpy(p, &men0.checksum, 8);
        
        // TX UART 0
        wordsWritten = write(pd0, buffer0, TAM_MAX);
        
        // MANUAL DELAY
        for (c = 1 ; c <= 32767 ; c++ ){
           for (d = 1 ; d <= 256; d++ ){}
           }
        
        // RX UART 1
        wordsRead = read(pd1, buffer1, TAM_MAX);
    
        // RECIEVE STRUCT
        p = buffer1;
        memcpy(&men1.Id, p, 4);
        res1.Id=men1.Id;
        p += 4;
        memcpy(&men1.Tam, p, 4);
        p += 4;
        memcpy(&men1.tiempo, p, 8);
        p += 8;    
        memcpy(&men1.Mensaje, p, men1.Tam);
        p += men1.Tam;
        memcpy(&men1.checksum, p, 8);
        cksum=0;
        for(j=0; j<(TAM_MAX-8); j++){
            cksum += (unsigned int)buffer1[j];
        }
    
        // OPEN-CREATE FILE
        fd1 = open("file_TX0_RX1.txt", O_WRONLY | O_CREAT | O_APPEND);
        if (fd1==-1){    
            res1.c ='f';
            printf("Fail to create/open file\n");
        } 
        else if(cksum == men1.checksum){
            res1.c = 'g';               // Checksum good
        }else{
            res1.c = 'b';               // Checksum bad
        }
        
        
        sprintf(prebuffer, "\n[ID %d|size %d|checksum %f|answer %c]\n", men1.Id, men1.Tam, men1.checksum,res1.c);
        write(fd1, prebuffer, strlen(prebuffer));
        write(fd1, men1.Mensaje, men1.Tam);
                
        gettimeofday(&t_act, NULL);
        
        if(t_ant.tv_sec!=0 && t_ant.tv_usec!=0){
        sprintf(prebuffer,"\n[Time between msg = %f]\n",
            (((t_act.tv_sec-t_ant.tv_sec)*1000000.0)+(t_act.tv_usec+t_ant.tv_usec)));
                
            write(fd1, prebuffer, strlen(prebuffer));
        }
        close(fd1);
        
        t_ant.tv_sec=t_act.tv_sec;
        t_ant.tv_usec=t_act.tv_usec;

        men0.Id++;            
    }
    // Close file descriptor & exit
    close(pd0);
    close(pd1);
    return 0;
} 
```

---

