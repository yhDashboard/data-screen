<template>
    <el-select v-model="value" placeholder="请选择" @change="change">
        <el-option
            v-for="item in options"
            :popper-append-to-body="false"
            :key="item.value"
            :label="item.label"
            :value="item.value"
        >
        </el-option>
    </el-select>
</template>

<script>
import create from "@/components/pool/create";
export default create({
    name: "selectFilter",
    data() {
        return {
            options: [
                {
                    value: "选项1",
                    label: "黄金糕",
                },
                {
                    value: "选项2",
                    label: "双皮奶",
                },
                {
                    value: "选项3",
                    label: "蚵仔煎",
                },
                {
                    value: "选项4",
                    label: "龙须面",
                },
                {
                    value: "选项5",
                    label: "北京烤鸭",
                },
            ],
            value: "",
        };
    },
    methods: {
      change(e) {
        let {id, option: {filterKey}} = this.instance
        this.pubsub.publish(id, {[filterKey]: e})
      }
    }
})
</script>

<style>
</style>