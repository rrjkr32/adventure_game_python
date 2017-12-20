# adventure_game_python
a mini game


                                    import random
                                    def main():
                                        dirs=(0,0,0,0)

                                        entrance={'name':'Entrance Way','directions':dirs,'msg':'You are in Entrance Way'}
                                        livingroom={'name':'Living Room','directions':dirs,'msg':'You are in Living Room'}
                                        hallway={'name':'Hallway','directions':dirs,'msg':'You are in Hallway'}
                                        kitchen={'name':'Kitchen','directions':dirs,'msg':'You are in Kitchen'}
                                        diningroom={'name':'Dining Room','directions':dirs,'msg':'You are in Dining Room '}
                                        familyroom={'name':'Family Room','directions':dirs,'msg':'You are in Family Room '}

                                        entrance['directions']=(kitchen,livingroom,0,0)
                                        livingroom['directions']=(diningroom,0,0,entrance)
                                        hallway['directions']=(0,kitchen,0,familyroom)
                                        kitchen['directions']=(0,diningroom,entrance,hallway)
                                        diningroom['directions']=(0,0,livingroom,kitchen)
                                        familyroom['directions']=(0,hallway,0,0)

                                        rooms=[livingroom,hallway,kitchen,diningroom,familyroom]
                                        room_with_eggs=random.choice(rooms)
                                        Flag=False
                                        room=entrance
                                        print("Welcome,Bunny can you find John\'s basket?")

                                        while True:
                                            idx=input("select a direction 'N','E','S'or'W':")
                                            while idx!='N' and idx!='E' and idx !='S' and idx!='W':
                                                idx=input("Sorry,that's an invalid choice,select a direction 'N','E','S'or'W':")
                                            direc=['N','E','S','W']
                                            print(direc.index(idx))
                                            x=int(direc.index(idx))

                                            if not room['directions'][x]:
                                                print("There is no way in that direction,")
                                                continue
                                            room=room['directions'][x]
                                            if Flag==False:
                                                if room['name']==room_with_eggs['name']:
                                                    Flag=True
                                                    print(room['msg']+"Put the eggs in the basket and reach back to entrance")
                                                    room['msg']="Your are back in "+room['name']+" You have already put the eggs,rush to entrance"
                                                else :
                                                    print("q")
                                                    print(room['msg'])
                                                    room['msg']="Your are back in "+room['name']
                                            else:
                                                 if room['name']=='Entrance Way':
                                                    print("You have dilivered the eggs and returned to entrance\nYou may leave \n Congrats!!!")
                                                    break
                                                 else:
                                                     print(room['msg'])
                                                     room['msg']="Your are back in "+room['name']


                                    main()         
