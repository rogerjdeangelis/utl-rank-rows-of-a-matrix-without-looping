# utl-rank-rows-of-a-matrix-without-looping
Rank Rows of a Matrix Without Looping 

    SAS Forum: Rank Rows of a Matrix Without Looping                                                                                
                                                                                                                                    
    Not as simple as you think                                                                                                      
                                                                                                                                    
       Two Solutions with different results                                                                                         
                                                                                                                                    
             a. Rank function in R                                                                                                  
             b. Oder funtion in R                                                                                                   
                                                                                                                                    
    SAS forum                                                                                                                       
    https://tinyurl.com/y6breknx                                                                                                    
    https://communities.sas.com/t5/SAS-IML-Software-and-Matrix/Rank-Rows-of-a-Matrix-Without-Looping/m-p/588380                     
                                                                                                                                    
    StackOverflow                                                                                                                   
    https://stackoverflow.com/questions/12289224/rank-and-order-in-r                                                                
                                                                                                                                    
    Sau Profile                                                                                                                     
    https://stackoverflow.com/users/6212271/sau                                                                                     
                                                                                                                                    
    *_                   _                                                                                                          
    (_)_ __  _ __  _   _| |_                                                                                                        
    | | '_ \| '_ \| | | | __|                                                                                                       
    | | | | | |_) | |_| | |_                                                                                                        
    |_|_| |_| .__/ \__,_|\__|                                                                                                       
            |_|                                                                                                                     
    ;                                                                                                                               
                                                                                                                                    
    options validvarname=upcase;                                                                                                    
    libname sd1 "d:/sd1";                                                                                                           
    data sd1.have;                                                                                                                  
      input v1-v3;                                                                                                                  
    cards4;                                                                                                                         
    6 9 5                                                                                                                           
    1 3 10                                                                                                                          
    0 0 0                                                                                                                           
    0 0 1                                                                                                                           
    0 1 1                                                                                                                           
    ;;;;                                                                                                                            
    run;quit;                                                                                                                       
                                                                                                                                    
                                                                                                                                    
    Up to 40 obs from SD1.HAVE total obs=5                                                                                          
                                                                                                                                    
      V1    V2    V3                                                                                                                
                                                                                                                                    
       6     9     5                                                                                                                
       1     3    10                                                                                                                
       0     0     0                                                                                                                
       0     0     1                                                                                                                
       0     1     1                                                                                                                
                                                                                                                                    
    *           _                                                                                                                   
     _ __ _   _| | ___  ___                                                                                                         
    | '__| | | | |/ _ \/ __|                                                                                                        
    | |  | |_| | |  __/\__ \                                                                                                        
    |_|   \__,_|_|\___||___/                                                                                                        
                         _                                                                                                          
      __ _      ___   __| | ___ _ __                                                                                                
     / _` |    / _ \ / _` |/ _ \ '__|                                                                                               
    | (_| |_  | (_) | (_| |  __/ |                                                                                                  
     \__,_(_)  \___/ \__,_|\___|_|                                                                                                  
                                                                                                                                    
                      | RULES                                                                                                       
                                                                                                                                    
      V1    V2    V3  |   V1          V2            V3                                                                              
                      |                                                                                                             
       6     9     5  |    3          1              2                                                                              
                                                                                                                                    
                         Index       Index         Index                                                                            
                         of          of            of                                                                               
                         Smallest=5  Middle val=6  Largest=9                                                                        
                                                                                                                                    
       1     3    10  |    1     2     3                                                                                            
       0     0     0  |    1     2     3                                                                                            
       0     0     1  |    1     2     3                                                                                            
       0     1     1  |    1     2     3                                                                                            
                                                                                                                                    
    *_                        _                                                                                                     
    | |__     _ __ __ _ _ __ | | __                                                                                                 
    | '_ \   | '__/ _` | '_ \| |/ /                                                                                                 
    | |_) |  | | | (_| | | | |   <                                                                                                  
    |_.__(_) |_|  \__,_|_| |_|_|\_\                                                                                                 
                                                                                                                                    
    ;                                                                                                                               
                                                                                                                                    
      V1    V2    V3  |     V1          V2        V3                                                                                
                      |                                                                                                             
       6     9     5  |    2.0         3.0       1.0  Same as above                                                                 
       1     3    10  |    1.0         2.0       3.0                                                                                
       0     0     0  |    2.0         2.0       2.0                                                                                
                      |                                                                                                             
       0     0     1  |    1.5         1.5       3.0                                                                                
                                                                                                                                    
                           Tie         Tie                                                                                          
                           Index       Index     Index                                                                              
                           of          of        of                                                                                 
                           Smallest=0  Middle=0  Largest=1                                                                          
                                                                                                                                    
       0     1     1  |    1.0         2.5       2.5                                                                                
                                                                                                                                    
    *            _               _                                                                                                  
      ___  _   _| |_ _ __  _   _| |_                                                                                                
     / _ \| | | | __| '_ \| | | | __|                                                                                               
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                               
                    |_|                                                                                                             
    ;                                                                                                                               
                                                                                                                                    
       work.wantOdr         work.wantRnt                                                                                            
      ===============    ==================                                                                                         
      V1    V2    V3       X1     X2     X3                                                                                         
                                                                                                                                    
       3     1     2      1.0    2.0    3.0                                                                                         
       1     2     3      2.0    3.0    1.0                                                                                         
       1     2     3      2.0    2.0    2.0                                                                                         
       1     2     3      1.5    1.5    3.0                                                                                         
       1     2     3      1.0    2.5    2.5                                                                                         
                                                                                                                                    
    *          _       _   _                                                                                                        
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                             
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                            
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                           
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                           
                                                                                                                                    
    ;                                                                                                                               
                                                                                                                                    
    %utl_submit_r64('                                                                                                               
      library(haven);                                                                                                               
      library(SASxport);                                                                                                            
      have=as.matrix(read_sas("d:/sd1/have.sas7bdat"));                                                                             
      have;                                                                                                                         
      wantrnk<-as.data.frame(t(apply(have, 1, rank)));                                                                              
      wantodr<-as.data.frame(t(apply(have, 1, order)));                                                                             
      write.xport(wantrnk,wantodr,file="d:/xpt/want.xpt");                                                                          
      wantrnk;                                                                                                                      
      wantodr;                                                                                                                      
    ');                                                                                                                             
                                                                                                                                    
                                                                                                                                    
    libname xpt xport "d:/xpt/want.xpt";                                                                                            
                                                                                                                                    
      proc copy in=xpt out=work;                                                                                                    
      run;quit;                                                                                                                     
                                                                                                                                    
    run;quit;                                                                                                                       
                                                                                                                                    
    NOTE: Input library XPT is sequential.                                                                                          
    NOTE: Copying XPT.WANTRNK to WORK.WANTRNK (memtype=DATA).                                                                       
    NOTE: BUFSIZE is not cloned when copying across different engines. System Option for BUFSIZE was used.                          
    NOTE: There were 5 observations read from the data set XPT.WANTRNK.                                                             
    NOTE: The data set WORK.WANTRNK has 5 observations and 3 variables.                                                             
    NOTE: Copying XPT.WANTODR to WORK.WANTODR (memtype=DATA).                                                                       
    NOTE: BUFSIZE is not cloned when copying across different engines. System Option for BUFSIZE was used.                          
    NOTE: There were 5 observations read from the data set XPT.WANTODR.                                                             
    NOTE: The data set WORK.WANTODR has 5 observations and 3 variables.                                                             
    NOTE: PROCEDURE COPY used (Total process time):                                                                                 
                                                                                                                                    
                                                                                                                                    
                                                                                                                                    
