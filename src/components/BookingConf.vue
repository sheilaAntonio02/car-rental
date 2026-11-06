<script>
export default {
    props: ['bookingConfirm', 'confirm'],
    emits: ['displayBooking', 'complete', 'gotoModal'],
    data() {
        return {

        }
    },
    methods: {
        triggerDisplayBooking() {
            this.$emit('displayBooking', this.bookingConfirm)
        },
        viewBookings(fullname, emailAdd, phoneNumber, pickUpLocation, dropOffLocation, DateOfService, AmountPayable, Duration, i) {
            this.$emit('complete', { name: fullname, email: emailAdd, number: phoneNumber, PickLoc: pickUpLocation, droploc: dropOffLocation, dateS: DateOfService, amount: AmountPayable, duration: Duration, price: i })
        },
        deleteBookConfirmation(page) {
            this.$emit('gotoModal', page)
        },
    }
}
</script>

<template>
    <div v-for="(con, index) in bookingConfirm" :key="index">
        <div class="w-full h-fit pb-10 flex justify-center items-center px-4 sm:px-6 lg:pl-50 pt-10 bg-sky-50">
            <div class="w-full max-w-4xl border border-orange-800 shadow-lg rounded-lg bg-gray-100">
                <div class="text-2xl py-4 px-6 bg-blue-400/20 text-orange-800 text-center font-bold uppercase">
                    Booking Confirmation
                </div>

                <!-- Responsive Flex Container: stacks on mobile, splits into two columns on medium screens -->
                <div
                    class="flex flex-col md:flex-row justify-center items-center md:items-start gap-6 md:gap-10 p-4 sm:p-6">
                    <div class="w-full md:w-auto">
                        <div>
                            <p class="text-gray-700 font-bold">Name:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.name }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Email Address:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.email }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Pick Up Location:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.PickLoc }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Date of Service:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.dateS }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Pick Up Time:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.PickLoc }}
                            </p>
                        </div>
                    </div>

                    <div class="w-full md:w-auto">
                        <div>
                            <p class="text-gray-700 font-bold">Phone Number:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.number }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Passenger:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.pass }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Drop Off Location:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.droploc }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Return Date of Service:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.returnD }}
                            </p>
                        </div>
                        <div>
                            <p class="text-gray-700 font-bold">Return Time:</p>
                            <p
                                class="px-3 py-3 mb-3 w-full md:w-90 h-10 rounded-md bg-gray-100 shadow-sm flex items-center overflow-hidden text-ellipsis whitespace-nowrap">
                                {{ con.returnT }}
                            </p>
                        </div>
                    </div>
                </div>

                <div v-for="add in confirm" :key="add">
                    <div
                        class="mb-4 px-6 sm:px-10 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2">
                        <p class="text-gray-700 font-bold">Total Cost: ₱{{ add.price }}</p>
                        <div class="flex items-center gap-5">
                            <div>
                                <p class="text-gray-700 font-bold">Service type: <span
                                        class="font-semibold text-gray-900">{{ add.name }}</span> </p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="flex items-center justify-center space-x-2 mb-4 px-4">
                    <button
                        @click="viewBookings(con.name, con.email, con.number, con.PickLoc, con.droploc, con.dateS, con.amount, con.duration, con.price)"
                        class="bg-orange-800 text-white py-2 px-4 rounded hover:bg-blue-400 focus:outline-none focus:shadow-outline"
                        type="submit">
                        Confirm
                    </button>
                    <button @click="deleteBookConfirmation(index)"
                        class="bg-orange-800 text-white py-2 px-4 rounded hover:bg-red-600 focus:outline-none focus:shadow-outline"
                        type="submit">
                        Cancel
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>