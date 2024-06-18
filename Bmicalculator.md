# OIBSIP
from tkinter import *
from tkinter import messagebox

def reset_entry():
    age_tf.delete(0,'end')
    height_tf.delete(0,'end')
    weight_tf.delete(0,'end')

def calculate_bmi():
    kg = int(weight_tf.get())
    m = int(height_tf.get())/100
    value = kg/(m*m)
    value = round(value,1)
    value_index(value)

def value_index(value):
    
    if value < 18.5:
        messagebox.showinfo('bmi-BMIcalculator', f'BMI = {value} is Underweight')
    elif (value > 18.5) and (value < 24.9):
        messagebox.showinfo('bmi-BMIcalculator', f'BMI = {value} is Normal')
    elif (value > 24.9) and (value < 29.9):
        messagebox.showinfo('bmi-BMIcalculator', f'BMI = {value} is Overweight')
    elif (value > 29.9):
        messagebox.showinfo('bmi-BMIcalculator', f'BMI = {value} is Obesity') 
    else:
        messagebox.showerror('bmi-BMIcalculator', 'OOPS...Something Went Wrong!')   

ws = Tk()
ws.title('BMIcalculator')
ws.geometry('700x800')
ws.config(bg='navy')

var = IntVar()

frame = Frame(
    ws,bg='DeepSkyBlue2',
    padx=60, 
    pady=70
)
frame.pack(expand=True)


age_lb = Label(
    frame,
    text="Enter Age",fg="red"
)
age_lb.grid(row=1, column=1)

age_tf = Entry(
    frame, 
)
age_tf.grid(row=1, column=2, pady=10)

gen_lb = Label(
    frame,
    text='Select Gender',fg="orange"
)
gen_lb.grid(row=2, column=1)

frame2 = Frame(
    frame
)
frame2.grid(row=2, column=2, pady=10)

male_rb = Radiobutton(
    frame2,
    text = 'Male',fg="blue",
    variable = var,
    value = 1
)
male_rb.pack(side=LEFT)

female_rb = Radiobutton(
    frame2,
    text = 'Female',fg="darkgreen",
    variable = var,
    value = 2
)
female_rb.pack(side=RIGHT)

height_lb = Label(
    frame,
    text="Enter Your Height (cm)  ",fg="brown"
)
height_lb.grid(row=3, column=1)

weight_lb = Label(
    frame,
    text="Enter Your Weight (kg)  ",fg="black"

)
weight_lb.grid(row=4, column=1)

height_tf = Entry(
    frame,
)
height_tf.grid(row=3, column=2, pady=10)

weight_tf = Entry(
    frame,
)
weight_tf.grid(row=4, column=2, pady=10)

frame3 = Frame(
    frame
)
frame3.grid(row=5, columnspan=3, pady=10)

cal_btn = Button(
    frame3,
    text='Calculate',fg="green",
    command=calculate_bmi
)
cal_btn.pack(side=LEFT)

reset_btn = Button(
    frame3,
    text='Reset',fg="purple",
    command=reset_entry
)
reset_btn.pack(side=LEFT)

exit_btn = Button(
    frame3,
    text='Exit',fg="darkblue",
    command=lambda:ws.destroy()
)
exit_btn.pack(side=RIGHT)

ws.mainloop()


