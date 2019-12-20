#include<string.h>  
#include<stdlib.h>
#include<stdio.h>  
#include<conio.h>  
typedef struct tagCustomer
{
  char m_ID[19];     /*身份证号码*/
  char m_name[10];   /*顾客姓名*/
  int  m_age;        /*顾客年龄*/
  char  m_sex[6];    /*顾客性别*/
  int num;
}Customer;/*顾客结构*/
 
typedef struct tagRoom
{
  int m_num;         /*房间号*/
  int m_floor;       /*楼层*/
  int m_price;       /*价格*/
  int m_use;         /*是否已入住*/
}Room;/*房间结构*/
int i,j=0,age,num,floor,price,use,n;
int reg =0;
Customer cus[5];
Room    r[5];
int count=5;
char ID[18],name[10],sex[6];
FILE *fproom;
FILE *fpcustomer;
 
void Customer_Input()
{
  if(count<=5)
  {
    printf("请输入身份证号(18位数字):");
    scanf("%s",&cus[j].m_ID);
    printf("请输入姓名(10位字符)");
    scanf("%s",&cus[j].m_name);
    printf("请输入年龄(数字型)");
    scanf("%d",&cus[j].m_age);
    printf("请输入性别(男或女):");
    scanf("%s",&cus[j].m_sex);
  }
  else
  {
    printf("\n 存储空间已满!");
  }
  printf("\n\r顾客可以住在:");
  printf("\n\r房间号   楼层   价格   是否空闲(1:空闲0：已使用)");
  for(i=0;i<count;i++)
  {
    if(r[i].m_use==1)
    {
      printf("\n\r%d      %d       %d       %d ",r[i].m_num,r[i].m_floor,r[i].m_price,r[i].m_use);
    }
  }
  printf("\n\r请你输入房间号:");
  scanf("%d",&num);
  reg = 0;
  for(i=0;i<count;i++)
  {
    if(r[i].m_use==1&&r[i].m_num==num)
    {
      r[i].m_use = 0;
      printf("\n 登记成功!\n");
      cus[j].num=r[i].m_num ;
      j=j+1;
      reg=1;
    }
  }
  if(reg==0)
  {
    printf("\n 登记失败!\n");
  }
   
}
void Customer_ListOut()
{
  if(count<=5)
  {
    printf("请输入身份证号(18位数字):");
    scanf("%s",&ID);
    for(i=0;i<count;i++)
    {
      if(strcmp(cus[i].m_ID,ID)==0)
      {
        printf("\n\r顾客身份证号：%s   姓名：%s   年龄：%d   性别：%s \n",cus[i].m_ID,cus[i].m_name,cus[i].m_age,cus[i].m_sex);
      }
    }
  }
  else
  {
    printf("\n \n");
  }
}
void Room_ListOut()
{
  printf("\n\r房间号   楼层   价格   是否空闲(1:空闲0：已使用)");
  for(i=0;i<count;i++)
  {
    if(r[i].m_use==1)
    {
      printf("\n\r%d      %d       %d       %d ",r[i].m_num,r[i].m_floor,r[i].m_price,r[i].m_use);
    }
  }
}
void PerCustomer_Search()
{
  if(count<=5)
  {
    printf("请输入身份证号(18位数字):");
    scanf("%s",&cus[j].m_ID);
    printf("请输入姓名(10位字符)");
    scanf("%s",&cus[j].m_name);
    printf("请输入年龄(数字型)");
    scanf("%d",&cus[j].m_age);
    printf("请输入性别(男或女):");
    scanf("%s",&cus[j].m_sex);
  }
  else
  {
    printf("\n 住房已满!");
  }
  printf("\n\r顾客可以预订:");
  printf("\n\r房间号   楼层   价格   是否空闲(1:空闲0：已使用)");
  for(i=0;i<count;i++)
  {
    if(r[i].m_use==1)
    {
      printf("\n\r%d      %d       %d       %d ",r[i].m_num,r[i].m_floor,r[i].m_price,r[i].m_use);
    }
  }
  printf("\n 请你输入要预订的房间号:");
  scanf("%d",&num);
  reg = 0;
  for(i=0;i<count;i++)
  {
    if(r[i].m_use==1&&r[i].m_num==num)
    {
      r[i].m_use = 0;
      printf("\n 预订成功!\n");
      cus[j].num=r[i].m_num ;
      j=j+1;
      reg=1;
    }
  }
  if(reg==0)
  {
    printf("\n 预订失败!\n");
  }
}
void UnCustomer_Out()
{
  int k;
  printf("\n 请输入要退房顾客身份证：");
        scanf("%s",&ID);
        for(i=0;i<count;i++)
        {
          if(strcmp(cus[i].m_ID,ID)==0)
          {
            printf("\n\r顾客身份证号：%s   姓名：%s   年龄：%d   性别：%s \n\r已经成功退房!",cus[i].m_ID,cus[i].m_name,cus[i].m_age,cus[i].m_sex);
            for(k=0;k<count;k++)
              if(r[k].m_num==cus[i].num)
                r[k].m_use=1;            
            memset(&cus[i],0,sizeof(Customer));
 
          }
        }
}
void Customer_Goaway()
{
  fproom=fopen("room","wb+");   
  fwrite((void *)&r,sizeof(Room),count,fproom);
  fclose(fproom);
   
  fpcustomer=fopen("customer","wb+");   
  fwrite((void *)&r,sizeof(Room),count,fpcustomer);
  fclose(fpcustomer); 
  exit(0);
   
}
main()
{
  fproom=fopen("room","wb");   
  if(fproom!=NULL)
  {
    for(i=0;i<count;i++)
    {
      int id=100;
      r[i].m_num=i+100;
      r[i].m_floor=1;
      r[i].m_price=100;
      r[i].m_use=1;
    }
    fwrite((void *)&r,sizeof(Room),count,fproom);
    fclose(fproom);
  }
  else
  {
    printf("\n---文件打开失败--");
  }   
  for(;;)
  {
     
    printf("\n");
    printf("/******************************************\\\n");
    printf("*                                          *\n");
    printf("*               酒店管理系统               *\n");
    printf("*                  主菜单                  *\n");
    printf("*                                          *\n");
    printf("*                1.顾客登记                *\n");
    printf("*                2.查询顾客信息            *\n");
    printf("*                3.查询空房间              *\n");
    printf("*                4.预订房间                *\n");
    printf("*                5.退订房间                *\n");
    printf("*                6.保存并退出系统          *\n"); 
    printf("*                                          *\n");
    printf("\\******************************************/\n\n");
    printf("请输入选择项(1-6):");
    scanf("%d",&n);
    printf("\n\n\n\n");
    if(n>0&&n<=6)
    {
      switch(n)
      {
      case 1:Customer_Input();break;
      case 2:Customer_ListOut();break;/*查询顾客信息*/
      case 3:Room_ListOut();break;/*查询空房间*/
      case 4:PerCustomer_Search();break;/*预订房间*/
      case 5:UnCustomer_Out();break;/*退订房间*/
      case 6:Customer_Goaway();  /*保存退出*/
      }
    }
    else 
    {
      printf("***********************************************************************\n");
      printf("*                                                                      *\n");
      printf("*                              输入错误!                               *\n");
      printf("*                              请退出!                                 *\n");
      printf("*                                                                      *\n");
      printf("***********************************************************************\n");
      break;
    }
  }
}
