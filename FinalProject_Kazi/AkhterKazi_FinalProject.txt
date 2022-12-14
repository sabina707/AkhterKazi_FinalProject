"""
File: AkhterKazi_FinalProject.py
Author: Kazi Sabina Akhter
Date:12/12/2022
Summary: Take online order for gourmat cake
Variables:
    dictionaries - themeList, flavorList, icingList, priceList:  for choice of theme,
                    flavor, icing and price(according to size)
    text field -  themeField, flavorField, icingField, sizeField, nameField, phoneField: for taking
                    input from user
import EasyFrame from breezypythongui
"""

from breezypythongui import EasyFrame


class gourmetCake(EasyFrame):
    def __init__(self):
        EasyFrame.__init__(self, title = "GourmetCake")
        self.setSize(600,700)

        # Dictionaries for theme, flavor, icing and price
        self.themeList = {
            "1" : "Spiderman",
            "2" : "Barbie",
            "3" : "Rainbow",
            "4" : "Flower",
            "5" : "Nature",
            "6" : "Bride-Groom",
            "7" : "Graduation",
            "8" : "Office theme",
            "9" : "Christmas"
            }
        self.flavorList = {
            "1" : "Vanilla",
            "2" : "Chocolate",
            "3" : "Velvet"
            }
        self.icingList = {
            "1" : "Cream cheese",
            "2" : "Whipped cream",
            "3" : "Fondant"
            }
        self.priceList = {
            "1" : "$25",
            "2" : "$35",
            "3" : "$50"
            }
        self.myWindow()

    # Draw window layout and fucntions
    def myWindow(self):
               
        
        # Panel and Label of introductions
        introPanel = self.addPanel(row = 0, column = 0,background = "#add8e6")

        introPanel.addLabel(text = "Delicious gourmet cake", row = 0, column =0,
                           sticky = "NSEW",font = ("Comic Sans MS",20),background = "#48AAAF")
        introPanel.addLabel(text = "Order you dream cake online", row = 1, column =0,
                           sticky = "NSEW",font = ("Comic Sans MS",12),background = "#48AACA")
        
        # Draw panel, label, and list box  for Occasion

        dataPanel = self.addPanel(row = 1, column = 0,background = "#add8e6")
        
        dataPanel.addLabel(text = "Occasions", row = 0, column = 0,
                               sticky = "EW", font = ("Comic Sans MS",12),background = "#add8e6")
        dataPanel.addLabel(text = " Birthday, Wedding, Other occasions \n Choose your theme",
                               row = 1, column = 0, sticky = "EW", background = "#add8e6")
        
        dataPanel.chooseTheme = dataPanel.addTextArea(text = " 1. Spiderman \n 2. Barbie \n "
                                                       "3. Rainbow \n 4. Flower \n 5. Nature \n 6. Bride-Groom"
                                                       "\n 7. Graduation \n 8. Office theme \n 9. Christmas" ,
                                              row = 0,column = 1, rowspan = 3, height = 5, width = 2)
        dataPanel.chooseTheme["state"] = "disabled"

        # Get user choice for occational theme
        self.themeField = dataPanel.addTextField(text = "", row = 2, column = 0, sticky = "EW")
            
        # Panel, label, and list box for flavor, icing, size

        dataPanel2 = self.addPanel(row = 2, column = 0,background = "#add8e6")              

        #
        dataPanel2.addLabel(text = "Flavors", row = 0, column = 0, sticky = "EW", background = "#6a5acd")
        dataPanel2.chooseFlavor = dataPanel2.addTextArea(text = " 1. Vanilla \n 2. Chocolate \n 3. Velvet",
                                               row = 1,column = 0, height = 2, width = 1)
        dataPanel2.chooseFlavor["state"] = "disabled"
        dataPanel2.addLabel(text = "Enter flavor no", row = 2, column = 0,
                               sticky = "EW", background = "#6a5acd")

        # Get user choice for flavor no
        self.flavorField = dataPanel2.addTextField(text = "", row = 3, column = 0, sticky = "EW")
                
        
        dataPanel2.addLabel(text = "Icing", row = 0, column = 1, sticky = "EW", background = "#6a5acd")
        dataPanel2.chooseIcing = dataPanel2.addTextArea(text = " 1. Cream cheese \n 2. Whipped cream \n 3. Fondant",
                                              row = 1,column = 1, height = 2, width = 2)
        dataPanel2.chooseIcing["state"] = "disabled"
        dataPanel2.addLabel(text = "Enter icing no", row = 2, column = 1,
                               sticky = "EW", background = "#6a5acd")

        # Get user choice for icing no
        self.icingField = dataPanel2.addTextField(text = "", row = 3, column = 1, sticky = "EW")
        

        dataPanel2.addLabel(text = "Size", row = 0, column = 2, sticky = "EW", background = "#6a5acd")
        dataPanel2.chooseSize = dataPanel2.addTextArea(text = " 1. 6 inch - $25 \n 2. 8 inch - $35 \n 3. 10 inch - $50",
                                              row = 1,column = 2, height = 2, width = 1)
        dataPanel2.chooseSize["state"] = "disabled"
        dataPanel2.addLabel(text = "Enter size no", row = 2, column = 2,
                               sticky = "EW", background = "#6a5acd")


        # Get user choice for size and price no
        self.sizeField = dataPanel2.addTextField(text = "", row = 3, column = 2, sticky = "EW")
        


        orderPanel = self.addPanel(row = 3, column = 0,background = "#add8e6")
        orderPanel.addLabel(text = "Please enter your name", row = 0, column = 0,
                               sticky = "EW", background = "#6a5acd")

        # Get user name
        self.nameField = orderPanel.addTextField(text = "", row = 0, column = 1, sticky = "EW")

        orderPanel.addLabel(text = "Please enter telephone no", row = 1, column = 0,
                               sticky = "EW", background = "#6a5acd")

        # Get user telephone no
        self.phoneField = orderPanel.addTextField(text = "", row = 1, column = 1, sticky = "EW")

        # Button for order confirmation
        orderPanel.addButton(text = "Place your order", row = 2, column = 0,columnspan = 2,
                             command = self.result)
    # Check for valid contact no
    def isContact_int(self,s):
        try:
            int(s)
            x = True
            return(x)
        except:
            x = False
            return(x)
           
 
    # Data velidate and show customer order confirmation   
    def result(self):
        
        # save user choices in different variables 
        theme = self.themeField.getText()
        flavor = self.flavorField.getText()
        icing = self.icingField.getText()
        size = self.sizeField.getText()
        cusName = self.nameField.getText()
        cusContactNo = self.phoneField.getText()

        validNo = self.isContact_int(cusContactNo)
        
        
        # Data validation for theme, flavor, icing, and size 
        if validNo and len(cusContactNo) == 10:
            if theme in (self.themeList)and flavor in (self.flavorList) and icing in (self.icingList) and size in (self.priceList):            
                message = ""
                message = "Hi "
                message += cusName + "\n"
                message += "Thanks for your order \n\n"
                message += "    Order details \n\n"
                message += "Theme: " + self.themeList[theme] + "\n"
                message += "Flavor: " + self.flavorList[flavor] + "\n"
                message += "Icing: " + self.icingList[icing] + "\n\n"
                message += "Total price " + self.priceList[size] + "\n\n"
                message += "Your order confirmation will send to you soon" 
        
                self.themeField["text"] = ""
                self.flavorField["text"]= ""
                self.icingField["text"]= ""
                self.sizeField["text"]= ""

                #show order confirmation or error through a message box
                self.messageBox(title = "Customer Order", message = message, height = 15, width = 30 )
                self.myWindow()
            else:
                self.messageBox(title = "Error in choice", message = "You choose wrong no \n"
                            "Please try again", height = 15, width = 30 )
                self.myWindow()
        else:
            self.messageBox(title = "Error", message = "Wrong contact no \n"
                            "Please enter valid contact no", height = 15, width = 30 )
            self.myWindow()
        

                
    
    
def main():
    """Instantiate and pop up the window."""
    gourmetCake().mainloop()

if __name__ == "__main__":
    try:
        while True:
            main()
    except KeyboardInterrupt:
        print("\nProgram closed.")
